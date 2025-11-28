# WORKING-STUDENT-MANAGEMENT-SYSTEM-C-PROJECT-
This Student Management System in C allows adding, viewing, searching, updating, and deleting student records using structures and arrays. It provides a simple console-based interface to manage roll numbers, names, and marks efficiently without file handling, making it ideal for beginners and mini-projects.

#include <stdio.h>
#include <string.h>

struct Student {
    long int roll;
    char name[50];
    float marks;
};

struct Student s[100];
int count = 0;

void addStudent() {
    printf("\nEnter Roll Number: ");
    scanf("%ld", &s[count].roll);

    printf("Enter Name: ");
    scanf(" %s", s[count].name);

    printf("Enter Marks: ");
    scanf("%f", &s[count].marks);

    count++;
    printf("Student Added Successfully!\n");
}

void viewStudents() {
    if (count == 0) {
        printf("\nNo students found!\n");
        return;
    }

    printf("\n---- Student List ----\n");
    for (int i = 0; i < count; i++) {
        printf("Roll: %ld | Name: %s | Marks: %.2f\n", 
                s[i].roll, s[i].name, s[i].marks);
    }
}

void searchStudent() {
    long int roll;
    printf("Enter Roll Number to Search: ");
    scanf("%ld", &roll);

    for (int i = 0; i < count; i++) {
        if (s[i].roll == roll) {
            printf("\nStudent Found:\n");
            printf("Roll: %ld\nName: %s\nMarks: %.2f\n", 
                    s[i].roll, s[i].name, s[i].marks);
            return;
        }
    }
    printf("Student Not Found!\n");
}

void updateMarks() {
    long int roll;
    printf("Enter Roll Number to Update: ");
    scanf("%ld", &roll);

    for (int i = 0; i < count; i++) {
        if (s[i].roll == roll) {
            printf("Enter New Marks: ");
            scanf("%f", &s[i].marks);
            printf("Marks Updated!\n");
            return;
        }
    }
    printf("Student Not Found!\n");
}

void deleteStudent() {
    long int roll, index = -1;

    printf("Enter Roll Number to Delete: ");
    scanf("%ld", &roll);

    for (int i = 0; i < count; i++) {
        if (s[i].roll == roll) {
            index = i;
            break;
        }
    }

    if (index == -1) {
        printf("Student Not Found!\n");
        return;
    }

    for (int i = index; i < count - 1; i++) {
        s[i] = s[i + 1];
    }

    count--;
    printf("Student Deleted Successfully!\n");
}

int main() {
    int choice;

    while (1) {
        printf("\n--- STUDENT MANAGEMENT SYSTEM ---\n");
        printf("1. Add Student\n2. View Students\n3. Search Student\n4. Update Marks\n5. Delete Student\n6. Exit\n");
        printf("Enter Choice: ");
        scanf("%ld", &choice);

        switch (choice) {
            case 1: addStudent(); break;
            case 2: viewStudents(); break;
            case 3: searchStudent(); break;
            case 4: updateMarks(); break;
            case 5: deleteStudent(); break;
            case 6: return 0;
            default: printf("Invalid Choice! Try again.\n");
        }
    }
}
