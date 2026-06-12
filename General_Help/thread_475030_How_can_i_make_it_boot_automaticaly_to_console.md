---
title: "How can i make it boot automaticaly to console ?"
date: 2007-06-15
forum: General Help
---

### Post by klol on 2007-06-15
I installed Ubuntu 7.04 using ubuntu-7.04-dvd-i386.iso. 
When it boots, it goes straight to gnome. 
How can i make it boot automaticaly to console ? 
I need it to boot to console in order to use it as a server, 
but i also need to be able to use gnome in some cases... 
So, i need to use startx when it boots to console, 
to load gnome.

---

### Post by kcbnac on 2007-06-15
Ubuntu has 8 'terminals' - often referred to as tty1, tty2, etc.

tty7 is what X starts in (you know this as Gnome) but you can use CTRL+ALT+F1 to switch to tty1, for example. (F1 = tty1, F2 = tty2, etc)

By default, every terminal except 7 is a 'terminal' or 'console' login, and you can switch between them on-the-fly, and be logged in as different users on each.  (Useful to pull up a browser in Gnome, with documentation, and then flip over to a console to run it)

---

### Post by parrottvision on 2007-07-31
I have installed server edition and I want it to start up to Gnome not terminal - how do I do that? 

I have also installed ubuntu-desktop and it is up to date.

How do I start up automatically to Gnome Desktop and not Terminal?

---

### Post by snooptodd on 2007-07-31
remove gdm

---

### Post by parrottvision on 2007-08-01
Nope - that aint right.

I did this instead:

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

Although I didnt get to enter the last line.

---

