#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Define structures for user and food items
typedef struct {
    char username[50];
    char password[50];
} User;

typedef struct {
    char name[100];
    float price;
} FoodItem;

// Function prototypes
void registerUser();
void loginUser();
void displayMenu();
void placeOrder(User user);
void viewOrderHistory(User user);

// Global variables
User currentUser;

// Sample menu
FoodItem menu[] = {
    {"Pizza", 10.99},
    {"Burger", 5.99},
    {"Pasta", 8.49},
    {"Salad", 6.99},
    {"Fries", 2.99}
};

int main() {
    int choice;

    printf("Welcome to the Online Food Delivery App!\n");

    do {
        printf("\n1. Register\n2. Login\n3. Display Menu\n4. Place Order\n5. View Order History\n6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                registerUser();
                break;
            case 2:
                loginUser();
                break;
            case 3:
                displayMenu();
                break;
            case 4:
                placeOrder(currentUser);
                break;
            case 5:
                viewOrderHistory(currentUser);
                break;
            case 6:
                printf("Thank you for using our app!\n");
                exit(0);
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while(1);

    return 0;
}

void registerUser() {
    printf("Enter your username: ");
    scanf("%s", currentUser.username);
    printf("Enter your password: ");
    scanf("%s", currentUser.password);
    printf("Registration successful!\n");
}

void loginUser() {
    char username[50];
    char password[50];

    printf("Enter your username: ");
    scanf("%s", username);
    printf("Enter your password: ");
    scanf("%s", password);

    if (strcmp(username, currentUser.username) == 0 && strcmp(password, currentUser.password) == 0) {
        printf("Login successful!\n");
    } else {
        printf("Invalid username or password!\n");
    }
}

void displayMenu() {
    printf("Menu:\n");
    for (int i = 0; i < sizeof(menu) / sizeof(menu[0]); i++) {
        printf("%d. %s - $%.2f\n", i + 1, menu[i].name, menu[i].price);
    }
}

void placeOrder(User user) {
    int choice;

    printf("Enter the number of the item you want to order: ");
    scanf("%d", &choice);

    if (choice >= 1 && choice <= sizeof(menu) / sizeof(menu[0])) {
        printf("Order placed successfully! Enjoy your %s!\n", menu[choice - 1].name);
    } else {
        printf("Invalid choice!\n");
    }
}

void viewOrderHistory(User user) {
    // Dummy function, as we are not storing order history in this simplified version
    printf("Order history:\n");
    printf("No orders placed yet.\n");
}

