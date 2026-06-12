---
title: "[SOLVED] What command is associated with a menu item from the main Application menu?"
date: 2007-12-22
forum: General Help
---

### Post by berliita on 2007-12-22
How to find out the command that gets executed, when i click a menu item in the main Application menu? I'd like to know it, so i can make a program launch on startup.

---

### Post by wormser on 2007-12-22
This example gets the command for the Calculator.

Right click on the Menu> Edit Menus> Select the folder (Accessories)> Select Calculator> Right click on it> Properties and you will see the command.  In this case it is gcalctool.

---

### Post by berliita on 2007-12-22
Thanks a lot, wormser. :)

And i'd like to add, for future reference, that the console command "which" retrieves the folder where the executable command file is located. In our example, typing: "$ which gcalctool" yields the output: "/usr/bin/gcalctool", which indicates that when you type the command "gcalctool" in the console, the file that gets executed is named "gcalctool" and is located inside the "/usr/bin/" folder.

---

