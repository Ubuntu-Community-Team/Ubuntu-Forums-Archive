---
title: "very new to ubuntu"
date: 2008-02-29
forum: General Help
---

### Post by v3problems on 2008-02-29
i have ubuntu 7.10, i think its gutsy gibbon.
on the forums i keep seeing that i have to enter a code or command, what does this mean? i want to install comiz fusion. please help, i have no idea where to start. 
thanks in advance for the help

---

### Post by steveneddy on 2008-02-29
Try going to the Desktop Effects & Customization area of the forums or

[this link]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy").

---

### Post by PinkFloyd102489 on 2008-02-29
Compiz Fusion is installed by default, however the config tool isnt.


Open a terminal and enter:

```

sudo apt-get install compizconfig-settings-manager

```


Then you can either launch it from a terminal with "ccsm" or under System > Preferences > Advanced Desktop Effects Settings.

---

### Post by v3problems on 2008-02-29
how do i open a terminal?

---

### Post by wireddad on 2008-02-29
One way is through Applications>Accessories>Terminal

---

### Post by pmaconi on 2008-02-29
Applications > Accessories > Terminal

---

### Post by wobbiebobbie on 2008-02-29
to open terminal go to application / accessories / and look for terminal

---

### Post by v3problems on 2008-02-29
> **PinkFloyd102489 said:**
> Compiz Fusion is installed by default, however the config tool isnt.


Open a terminal and enter:

```

sudo apt-get install compizconfig-settings-manager

```


Then you can either launch it from a terminal with "ccsm" or under System > Preferences > Advanced Desktop Effects Settings.

if i put that into the terminal it asks me for a password, i try to in the password i use t login but i cant put it there

---

### Post by wireddad on 2008-02-29
You should have created a root password.  Do you remember?

---

### Post by steveneddy on 2008-02-29
> **v3problems said:**
> if i put that into the terminal it asks me for a password, i try to in the password i use t login but i cant put it there

You won't see the password as you are typing it in.

---

### Post by v3problems on 2008-02-29
ok, got the password thing.
sorry but i am just starting to use ubuntu

---

### Post by v3problems on 2008-02-29
how do i make the desktop cube thing?

---

### Post by Victormd on 2008-02-29
Considering that you've installed compizconfig-settings-manager, go to System>Preferences>Advanced desktop effects settings

You'll see an icon (a cube) "Desktop Cube" mark it. The configuration manager will ask if you want to disable desktop wall, just answer yes. Next, mark "Rotate Cube" (don't click on the icon, click on the check box). Now you'll have the cube and the ability to rotate it but wait, you only have 2 workspaces configured. Click on "General Options">Desktop size and set the Horizontal Virtual size to 4. Or, you can close all the windows, and on the bottom right, you'll see two rectangles and if you move your cursor over them, you'll see something like "Current Workspace", right click on it, select preferences, choose 4 columns and close. Now you have a cube...

You can play around with the settings once you have the cube by going to the Advanced desktop settings and clicking over the icon.

---

### Post by pmaconi on 2008-02-29
System > Preferences > Advanced Desktop Settings

Click the button that says "General" and choose the Desktop Size tab. Set the Horizontal Virtual Size to 4. Press Back. Under "Desktop" enable the Desktop Cube and Rotate Cube options. You can now hold Alt + Ctrl and move the cube around by clicking and dragging with your mouse.

You may additionally want to enable Cube Gears and Cube Reflection under the Effects section. There is also Cube Caps under utility.

---

