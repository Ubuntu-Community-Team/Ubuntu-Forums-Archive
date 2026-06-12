---
title: "How do I get Icons for programs i install?"
date: 2008-06-13
forum: General Help
---

### Post by morbid_bean on 2008-06-13
I just installed Lynx and im wondering how i can get the icon to show up in my applications>internet menu....the only way i can load it is the terminal.

---

### Post by latna on 2008-06-13
Lynx is a console based browser. I'm not quite sure if you're aware of that or not. So you have to open up a terminal to run it anyway. Of course you could open the menu editor and make an entry for it. Enter this for the application to run:
```
xterm -e lynx
```

---

### Post by spiderbatdad on 2008-06-13
Go to System>>Preferences>>Main Menu. On the left side of the window, select "Internet." Then on the right side, click "New Item." Input a name in the name field, and the command you use in the terminal, in the command field. Save. Voila.

You can right click on the new item in the Main Menu, and select properties. Then click on the icon in the upper left hand corner on the properties dialog box to select a different icon, if you like.

---

### Post by morbid_bean on 2008-06-13
> **spiderbatdad said:**
> Go to System>>Preferences>>Main Menu. On the left side of the window, select "Internet." Then on the right side, click "New Item." Input a name in the name field, and the command you use in the terminal, in the command field. Save. Voila.

You can right click on the new item in the Main Menu, and select properties. Then click on the icon in the upper left hand corner on the properties dialog box to select a different icon, if you like.

Thanks alot!

---

