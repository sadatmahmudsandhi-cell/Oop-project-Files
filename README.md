# Oop-project-Files
Contains a presentation and 3 java code files
import java.util.ArrayList;
import java.util.Scanner;

// Abstraction
abstract class Item {
    abstract void show();
}

// Encapsulation + Inheritance
class Product extends Item {
    private String name;
    private String id;

    Product(String name, String id) {
        this.name = name;
        this.id = id;
    }

    public void show() {
        System.out.println("Product Name: " + name);
        System.out.println("Product ID: " + id);
    }
}

// Inheritance
class Service extends Item {
    private String name;

    Service(String name) {
        this.name = name;
    }

    public void show() {
        System.out.println("Service: " + name);
    }
}

public class Main {

    public static void main(String[] args) {

        ArrayList<Item> list = new ArrayList<>();
        Scanner sc = new Scanner(System.in);

        while (true) {

            System.out.println("\n1. Add Product");
            System.out.println("2. Add Service");
            System.out.println("3. Show All");
            System.out.println("4. Exit");

            System.out.print("Enter choice: ");
            int choice = sc.nextInt();

            // Polymorphism (runtime)
            if (choice == 1) {

                System.out.print("Enter Product Name: ");
                String name = sc.next();

                System.out.print("Enter Product ID: ");
                String id = sc.next();

                list.add(new Product(name, id));

            } 
            else if (choice == 2) {

                System.out.print("Enter Service Name: ");
                String name = sc.next();

                list.add(new Service(name));

            } 
            else if (choice == 3) {

                for (Item i : list) {
                    i.show();   // Polymorphism
                    System.out.println();
                }

            } 
            else if (choice == 4) {
                System.out.println("Exit...");
                break;
            } 
            else {
                System.out.println("Invalid choice!");
            }
        }
    }
}
