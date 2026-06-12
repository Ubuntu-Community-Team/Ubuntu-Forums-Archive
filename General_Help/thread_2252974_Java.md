---
title: "Java"
date: 2014-11-16
forum: General Help
---

### Post by 0N3 on 2014-11-16
I am working on a project for college drinks ordering system I have to autogenerate the drinkId which works fine it starts and 101 and increments from there. When I close and reopen my program after writing to a file called output.dat I read back in output.dat but it then starts drinkId at 101 again and increments from there any ideas how to solve this? Sorry if this is posted in the wrong place!

```
package ie.drink.wit;

import java.io.Serializable;
import java.util.ArrayList;
import java.util.List;


public class Drinks implements Serializable {


    // Declare variables
    List<Drinks> aList = new ArrayList<Drinks>();
    private int drinkId = nextId++;
    private static int nextId = 101;
    private String company;
    private String name;
    private double price;
    private int qty;
    private double totalCost;


    public Drinks(int drinkId, String company, String name, double price,
            int qty) {
        this.drinkId = nextId++;
        this.company = company;
        this.name = name;
        this.price = price;
        this.qty = qty;
    }


    public Drinks() {


    }


    // Getters and Setters for Drinks
    public String getCompany() {
        return company;
    }


    public void setCompany(String company) {
        this.company = company;
    }


    public int getDrinkId() {
        return drinkId;
    }


    public void setDrinkId(int drinkId) {
        this.drinkId = drinkId;
    }


    public String getName() {
        return name;
    }


    public void setName(String name) {
        this.name = name;
    }


    public int getQuantity() {
        return qty;
    }


    public void setQuantity(int qty) {
        this.qty = qty;
    }


    public double getPrice() {
        return price;
    }


    public void setPrice(double price) {
        this.price = price;
    }


    public double getTotalCost() {
        return totalCost;
    }


    public void setTotalCost(double totalCost) {
        this.totalCost = price * qty;
    }


    // To String Method to print product details to the user


    public String toString() {


        return "Company: " + company + "  Drink ID: " + drinkId
                + "  Drink Name: " + name + "  Drink Price: " + price
                + "  Quantity: " + qty + "  Total Cost: €" + price * qty + "\n";
    }
}
```

---

