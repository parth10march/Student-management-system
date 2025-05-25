# Student-management-system

import java.util.ArrayList;
import java.util.Scanner;

// Class representing a student
class Student {
    int id;  // Unique student ID
    String name;  // Student's name
    int age;  // Student's age
    
    // Constructor to initialize student details
    Student(int id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }
    
    // Overriding toString method to display student information
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Age: " + age;
    }
}

// Main class to manage student records
public class Main {
    static ArrayList<Student> students = new ArrayList<>();  // List to store student records
    static Scanner scanner = new Scanner(System.in);  // Scanner for user input

    // Method to add a new student record
    public static void addStudent() {
        System.out.print("Enter ID: ");
        int id = scanner.nextInt();
        scanner.nextLine(); // Consume newline
        System.out.print("Enter Name: ");
        String name = scanner.nextLine();
        System.out.print("Enter Age: ");
        int age = scanner.nextInt();
        
        students.add(new Student(id, name, age));  // Adding student to the list
        System.out.println("Student added successfully!");
    }

    // Method to display all student records
    public static void displayStudents() {
        if (students.isEmpty()) {
            System.out.println("No records found.");
            return;
        }
        // Loop through the list to display each student
        for (Student student : students) {
            System.out.println(student);
        }
    }

    // Method to delete a student record by ID
    public static void deleteStudent() {
        System.out.print("Enter ID of student to delete: ");
        int id = scanner.nextInt();
        
        // Removing student if their ID matches
        students.removeIf(student -> student.id == id);
        System.out.println("Student removed successfully!");
    }

    // Main method - Entry point of the program
    public static void main(String[] args) {
        while (true) { // Infinite loop until user exits
            System.out.println("\nStudent Record Management System");
            System.out.println("1. Add Student");
            System.out.println("2. Display Students");
            System.out.println("3. Delete Student");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            
            // Handling user choices using switch statement
            switch (choice) {
                case 1 -> addStudent();  // Calls method to add student
                case 2 -> displayStudents();  // Calls method to display students
                case 3 -> deleteStudent();  // Calls method to delete student
                case 4 -> {  // Exit condition
                    System.out.println("Exiting...");
                    return;
                }
                default -> System.out.println("Invalid choice, try again.");  // Handles invalid input
            }
        }
    }
}
