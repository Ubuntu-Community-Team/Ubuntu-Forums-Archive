---
title: "Default boot to Vista"
date: 2008-06-18
forum: General Help
---

### Post by alokrsx on 2008-06-18
I'm having both Windows Vista and Ubuntu on my laptop. But the problem is that it automatically loads Ubuntu after showing in the boot menu in a few seconds.
What I want to do is that I want Vista to load automatically under a few seconds in the boot menu without pressing the down arrow and highlighting Vista and pressing enter key. How do I do this?

---

### Post by helino on 2008-06-18
First, when you're starting your computer, remember which row that Windwos Vista is on (for example 2). **Remeber that the first row is number 0!**

Now you have to change menu.lst, located in 
/boot/grub/menu.lst. To do this, you need to use sudo and a texteditor:

```
sudo gedit /boot/grub/menu.lst
```

In the file, you will see *default* and then a number. Change the number to the row that Windows Vista was on (in my example row number 2).

Save, and the next time you boot your computer, it will by default boot into Windows Vista.

---

### Post by Kevbert on 2008-06-18
Enter 
```
sudo gedit /boot/grub/menu.lst
```
In the menu.lst file you need to look for 
```
default 0
```
Counting from zero find the number equivalent to the menu item for Vista, include the line 
```
Other operating systems  
```
as a menu item.  Now change the default line to that number
```
default 4
```

---

### Post by alokrsx on 2008-06-20
^Thanks a lot, that helped. :)

---

