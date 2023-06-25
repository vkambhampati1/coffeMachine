# coffeMachine
/* *****************************************************************************
 *  Name:              Ada Lovelace
 *  Coursera User ID:  123456
 *  Last modified:     October 16, 1842
 **************************************************************************** */

package com.hyperskill;

import java.util.Scanner;

public class CoffeMachine {
    private static int water = 400;
    private static int milk = 540;
    private static int coffeeBeans = 120;
    private static int disposableCups = 9;
    private static int money = 550;


    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Write action (buy, fill, take, remaining, exit):");
            String action = scanner.next();
            switch (action) {
                case "buy":
                    buyCoffee(scanner);
                    break;
                case "fill":
                    fillMachine(scanner);
                    break;
                case "take":
                    takeMoney();
                    break;
                case "remaining":
                    printRemaning();
                    break;
                case "exit":
                    return;
            }

        }

    }

    private static void printRemaning() {
        System.out.println("The coffee machine has:");
        System.out.println(water + " ml of water");
        System.out.println(milk + " ml of milk");
        System.out.println(coffeeBeans + " g of coffee beans");
        System.out.println(disposableCups + " disposable cups");
        System.out.println("$" + money + " of money");

    }

    private static void buyCoffee(Scanner scanner) {
        System.out.println(
                "What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:");
        String choice = scanner.next();

        switch (choice) {
            case "1":  // espresso
                makeCoffee(250, 0, 16, 4);
                break;
            case "2":  // latte
                makeCoffee(350, 75, 20, 7);
                break;
            case "3":  // cappuccino
                makeCoffee(200, 100, 12, 6);
                break;
            case "back":
                break;
        }
    }

    private static void makeCoffee(int waterRequired, int milkRequired, int coffeeBeansRequired,
                                   int cost) {
        String msg = water < waterRequired
                     ? "Sorry, not enough water!"
                     : milk < milkRequired
                       ? "Sorry, not enough milk!"
                       : coffeeBeans < coffeeBeansRequired
                         ? "Sorry, not enough coffee beans!"
                         : disposableCups < 1
                           ? "Sorry, not enough disposable cups!"
                           : "I have enough resources, making you a coffee!";
        System.out.println(msg);

        water = -waterRequired;
        milk = -milkRequired;
        coffeeBeans = -coffeeBeansRequired;
        disposableCups--;
        money += cost;
    }

    private static void fillMachine(Scanner scanner) {
        System.out.println("Write how many ml of water you want to add:");
        int addWater = scanner.nextInt();
        System.out.println("Write how many ml of milk you want to add:");
        int addMilk = scanner.nextInt();
        System.out.println("Write how many grams of coffee beans you want to add:");
        int addCoffeeBeans = scanner.nextInt();
        System.out.println("Write how many disposable cups you want to add:");
        int addDisposableCups = scanner.nextInt();

        water += addWater;
        milk += addMilk;
        coffeeBeans += addCoffeeBeans;
        disposableCups += addDisposableCups;
    }

    private static void takeMoney() {
        System.out.println("I gave you $" + money);
        money = 0;
    }
}
