---
title: "Change default size of Terminal Window?"
date: 2007-06-05
forum: General Help
---

### Post by andrew.46 on 2007-06-05
Hi,

 Is there a way of changing the default size of a Terminal window? I would like it to open up to fill about 80% of my screen rather than the current 20% or so.

 I use slrn and it drives me a little crazy having to resize the window each time I set the program running. Perhaps I need to get out a little more :-)

                   Andrew

---

### Post by strabes on 2007-06-06
KDE has window size, location, desktop, etc options built in. I don't know if you can do it natively in gnome. Considered switching?

---

### Post by freakavoid on 2007-06-06
There is always [devilspie]("http://wiki.foosel.net/linux/devilspie").

But if you want to do it natively you can try the wmctrl command. Something like 

```

#!/bin/bash
gnome-terminal&
sleep 1s;
wmctrl -r Gnome-terminal -e "0,x,y,w,h" -x

```

will open a terminal window with the top left corner at (x,y) coordinate with a width of w and a hight of h. You can alter the detection of the window for your particular app. Take a look at the manpage of wmctrl.

---

### Post by Z-Funk on 2008-01-19
> **andrew.46 said:**
> Hi,

 Is there a way of changing the default size of a Terminal window? I would like it to open up to fill about 80% of my screen rather than the current 20% or so.

 I use slrn and it drives me a little crazy having to resize the window each time I set the program running. Perhaps I need to get out a little more :-)

                   Andrew

The default size of the gnome terminal window in Ubuntu can be modified by editing
/usr/share/applications/gnome-terminal.desktop
This apparently is the file that is parsed when you select
Applications->System Tools->Terminal
Editing this file will affect the menu for all users on that machine.

What I did was modify the Exec= entry to read:
Exec=gnome-terminal --geometry=120x30
You need to be root to edit this file.

---

### Post by stchman on 2008-02-18
> **Z-Funk said:**
> The default size of the gnome terminal window in Ubuntu can be modified by editing
/usr/share/applications/gnome-terminal.desktop
This apparently is the file that is parsed when you select
Applications->System Tools->Terminal
Editing this file will affect the menu for all users on that machine.

What I did was modify the Exec= entry to read:
Exec=gnome-terminal --geometry=120x30
You need to be root to edit this file.

No, you can edit the .desktop files by accessing the menus from the Edit Menus by right mouse clicking the Applications and editing the Terminal in Accessories.

---

### Post by slughappy1 on 2008-03-04
Is there a way to make a keyboard shortcut load a terminal with a specific size? I edited the Exec=gnome-terminal --geometry=140x25 but when I use the keyboard shortcut it loads the normal size terminal.

---

### Post by noynac on 2008-03-04
> **slughappy1 said:**
> Is there a way to make a keyboard shortcut load a terminal with a specific size? I edited the Exec=gnome-terminal --geometry=140x25 but when I use the keyboard shortcut it loads the normal size terminal.

Can't you just use the following command in the shortcut:

gnome-terminal --geometry=140x25

---

### Post by slughappy1 on 2008-03-04
Well what I did was ```
sudo nano /usr/share/applications/gnome-terminal.desktop
```
I found the line
```
Exec=gnome-terminal
``` 
and changed it to 
```
gnome-terminal --geometry=140x25
```
I also have, in System -> Preferences -> Keyboard Shortcuts, Run a Terminal set to Alt + t. When I use the shortcut it loads the normal geometry, but if I go to Applications -> Accessories -> Terminal, it loads the terminal with the 140x25 geometry

---

### Post by lpanebr on 2008-06-11
I do it with compiz:

on the "Window Rules" plugin I set the window size and make it appear on all viewpoorts (sticky) - see screenshot

on the "Place Windows" plugin I set the position I like it to appear  - see screenshot

**Note:** by default ubuntu does not come with the Compiz Config Settings Manager, however its realy easy to install it. There are 2 easy ways:
[INDENT]**from Synaptic:**
FIND "compizconfig-settings-manager" package, MARK it and click APPLY[/INDENT]
or
[INDENT]**from the shell:**
sudo apt-get install compizconfig-settings-manager[/INDENT]

***Doing it like that will allways open the terminal the way you want, no matter how you do it, menu or keyboard shortcut.***

**Now I have a question of my own:** How to set a keyboard shortcut to just switch to an already open terminal window?

---

### Post by AlexStojan on 2008-06-28
You can do it by simply right-clicking on the Terminal icon, go to Properties and in the Command section just add --geometry XxY. On my system it looks like this: gnome-terminal --geometry 120x50.

P.S. I'm using Ubuntu 7.10

---

### Post by lpanebr on 2008-06-29
Changing it with the --geometry on the icon properties will only affect terminals opened using that icon, while the compiz option will allways resize every terminal you open (as I posted earlier)

A couple weeks ago I learned of wmctrl (a program that that lets you control windows) and now I have a nice script that gives me a Quake Terminal whenever I hit Ctrl+F9! Its very handy.

Check it out on this other post.

[http://ubuntuforums.org/showthread.php?p=5208248#post5208248](http://ubuntuforums.org/showthread.php?p=5208248#post5208248)

hope it helps.

---

