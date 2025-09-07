# Python To-Do List

A simple command-line To-Do List application in Python.  
You can **view**, **add**, and **delete** tasks interactively.

## Features
- View all tasks
- Add new tasks
- Delete tasks by number
- Console-friendly with clear screen after each action

import os

# Initialize an empty todo list
todo_list = []

def clear_screen():
    """Clear the console screen."""
    os.system('cls' if os.name == 'nt' else 'clear')

def show_tasks():   # """Display all tasks in the todo list."""
   
    if not todo_list:
        print("No tasks yet")
    else:
        for i, task in enumerate(todo_list, 1):
            print(f"{i}. {task}")

def add_task(task):
    """Add a new task to the todo list."""
    todo_list.append(task)
    print("Task added")

def delete_task(index):        # """Delete a task by its number."""
    
    if 0 < index <= len(todo_list):
        removed = todo_list.pop(index - 1)
        print(f"Deleted: {removed}")
    else:
        print("Enter a valid number")

# Main loop
while True:
    clear_screen()
    print("== TO-DO LIST ==")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Delete Task")
    print("4. Exit")

    try:
        choice = int(input("Choose an option (1-4): "))
    except ValueError:
        print("Invalid input! Please enter a number 1-4.")
        input("\nPress Enter to continue...")
        print("\n")
        continue

    if choice == 1:
        show_tasks()
        input("\nPress Enter to continue...")
    elif choice == 2:
        task = input("Enter the task: ")
        add_task(task)
        input("\nPress Enter to continue...")
    elif choice == 3:
        try:
            index = int(input("Enter the task number to delete: "))
            delete_task(index)
        except ValueError:
            print("Enter a valid number")
        input("\nPress Enter to continue...")
    elif choice == 4:
        print("GoodBye 👋")
        break
    else:
        print("Invalid Option")
        input("\nPress Enter to continue...")

    print("\n")  # gap after every loop
