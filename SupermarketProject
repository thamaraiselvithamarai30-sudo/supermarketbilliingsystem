import java.util.*;
import java.text.SimpleDateFormat;

class Item {
    String name;
    double price;

    Item(String name, double price) {
        this.name = name;
        this.price = price;
    }
}

public class SupermarketProject {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Item[] items = {
            new Item("Milk", 40),
            new Item("Bread", 30),
            new Item("Rice", 60),
            new Item("Eggs (per piece)", 6),
            new Item("Oil (1L)", 150)
        };

        int[] quantities = new int[items.length];

        System.out.println("=== SUPERMARKET BILLING SYSTEM ===");
        System.out.print("Enter Customer Name: ");
        String customerName = sc.nextLine();
        int billNo = (int)(Math.random() * 10000);

        int choice;
        do {
            System.out.println("\n--- MENU ---");
            System.out.println("1. Show Items");
            System.out.println("2. Add to Cart");
            System.out.println("3. View Cart");
            System.out.println("4. Checkout and Exit");
            System.out.print("Choose an option: ");
            choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("\nAvailable Items:");
                    for (int i = 0; i < items.length; i++) {
                        System.out.println((i + 1) + ". " + items[i].name + " - Rs." + items[i].price);
                    }
                    break;

                case 2:
                    System.out.print("Enter item number to buy: ");
                    int itemNo = sc.nextInt();
                    if (itemNo < 1 || itemNo > items.length) {
                        System.out.println("Invalid item number ❌");
                        break;
                    }
                    System.out.print("Enter quantity for " + items[itemNo - 1].name + ": ");
                    int qty = sc.nextInt();
                    quantities[itemNo - 1] += qty;
                    System.out.println(qty + " " + items[itemNo - 1].name + " added to cart ✅");
                    break;

                case 3:
                    double total = 0;
                    boolean empty = true;
                    System.out.println("\nItems in Cart:");
                    for (int i = 0; i < items.length; i++) {
                        if (quantities[i] > 0) {
                            double itemTotal = items[i].price * quantities[i];
                            total += itemTotal;
                            System.out.println(items[i].name + " x " + quantities[i] + " = Rs." + itemTotal);
                            empty = false;
                        }
                    }
                    if (empty) {
                        System.out.println("Cart is empty ❌");
                    } else {
                        System.out.println("Current Total = Rs." + total);
                    }
                    break;

                case 4:
                    printBill(items, quantities, customerName, billNo);
                    break;

                default:
                    System.out.println("Invalid option ❌");
            }

        } while (choice != 4);

        sc.close();
    }

    public static void printBill(Item[] items, int[] quantities, String customerName, int billNo) {
        double total = 0;
        boolean empty = true;

        Date date = new Date();
        SimpleDateFormat formatter = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

        System.out.println("\n===== FINAL BILL =====");
        System.out.println("Bill No: " + billNo);
        System.out.println("Customer: " + customerName);
        System.out.println("Date: " + formatter.format(date));
        System.out.println("----------------------------");

        for (int i = 0; i < items.length; i++) {
            if (quantities[i] > 0) {
                double itemTotal = items[i].price * quantities[i];
                total += itemTotal;
                System.out.println(items[i].name + " x " + quantities[i] + " = Rs." + itemTotal);
                empty = false;
            }
        }

        if (empty) {
            System.out.println("Cart is empty. Nothing to checkout ❌");
        } else {
            double discount = (total > 1000) ? total * 0.10 : 0;
            double gst = (total - discount) * 0.05;
            double finalAmount = total - discount + gst;

            System.out.println("----------------------------");
            System.out.println("Total = Rs." + total);
            System.out.println("Discount = Rs." + discount);
            System.out.println("GST (5%) = Rs." + gst);
            System.out.println("----------------------------");
            System.out.println("Grand Total = Rs." + finalAmount);
            System.out.println("============================");
            System.out.println("   THANK YOU, VISIT AGAIN!  ");
            System.out.println("============================");
        }
    }
}
