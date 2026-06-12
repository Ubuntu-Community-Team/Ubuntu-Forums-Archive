---
title: "Root in the welcome screen"
date: 2007-02-10
forum: General Help
---

### Post by telovoyagarcar on 2007-02-10
Im so pissed of having to type "sudo" every minute i use Ubuntu, and also makes using the GUI more complicated when i want to edit any file in /etc. 
Do not worry about being an insecure practice to use root as the main user, because it is my laptop and i dont care if anything happens. All my important stuff is in my desktop.

There is a line in the gdm.conf file that i changed to "true".. (allow root login) but i can not login with root from the gnome welcome screen. There should be a way to do this.

Where should i look?

Thanks guys

---

### Post by llamakc on 2007-02-10
Why not just enable root?

sudo passwd root

(enter your password)

Now, enter a password for the root user.

Next,

use `su -` to get a root prompt.

---

### Post by Maestro23 on 2007-02-10
.

---

### Post by TheWizzard on 2007-02-10
```
sudo -s
```

---

### Post by 23meg on 2007-02-10
System / Administration / Login Window / Security / Allow local system administration login

---

### Post by blair on 2007-02-14
If for some reason you cannot access the Login Window preferences from the menu system, launch gdmsetup directly from the command line:

sudo gdmsetup

While the problem you are trying to solve can be addressed within gdmsetup, as per /etc/gdm/gdm.conf, not all possible GDM settings can be accessed via the gdmsetup GUI.  You may need to directly edit /etc/gdm/gdm.conf-custom (which overwrites /etc/gdm/gdm.conf).

---

### Post by dcstar on 2007-02-14
> **telovoyagarcar said:**
> Im so pissed of having to type "sudo" every minute i use Ubuntu, and also makes using the GUI more complicated when i want to edit any file in /etc. 
Do not worry about being an insecure practice to use root as the main user, because it is my laptop and i dont care if anything happens. All my important stuff is in my desktop.

There is a line in the gdm.conf file that i changed to "true".. (allow root login) but i can not login with root from the gnome welcome screen. There should be a way to do this.

Where should i look?

Thanks guys

Make a launcher with the following:
```
gksudo nautilus
```
Then you can browse files with root privileges and open, edit, delete, whatever......

---

### Post by Zaxor the other @ss isn't on 2007-02-15
here is the mess I get when I try this

zaxor@zaxor-desktop:~$ su
Password:
root@zaxor-desktop:/home/zaxor# sudo gdmsetup
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gdmsetup:5988): Gtk-WARNING **: cannot open display:
root@zaxor-desktop:/home/zaxor# gksudo nautilus
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gksudo:6008): Gtk-WARNING **: cannot open display:
root@zaxor-desktop:/home/zaxor#


 this happens everytime I install kubuntu in conjunction with ubuntu
it also stops me from going to "system, Administration, Login Window" it prompts for password then never shows up...and when I changed it before I installed Kubuntu to allow Root login I was allowed to login as root but after installing Kubuntu I am no longer allowed. 

a little help from you wizards and wizdresses would be greatly appreciated

---

