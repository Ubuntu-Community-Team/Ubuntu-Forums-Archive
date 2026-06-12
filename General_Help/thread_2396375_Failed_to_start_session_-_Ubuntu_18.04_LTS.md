---
title: "Failed to start session - Ubuntu 18.04 LTS"
date: 2018-07-14
forum: General Help
---

### Post by retrorelix on 2018-07-14
I upgraded from Ubuntu 17.10 to 18.04 over the update-manager. After the installation I'm not able to log in anymore. I just get a "Failed to start session"-text when entering my password.
I tried to install ubuntu-desktop```
sudo apt-get install ubuntu-desktop
```
but there are unmet dependencies and it looks like all these dependent packages have unmet dependencies too...

Does anyone know how to fix this problem?

---

### Post by ajgreeny on 2018-07-14
Check that you have the ubuntu-session package installed with ```
dpkg -s ubuntu-session
``` and add it if not already installed.

---

### Post by retrorelix on 2018-07-15
It is not installed.
I tried to install it with apt-get... but it could not be installed because of unmet dependencies (gnom-shell, gnome-session-bin not going to be installed).

---

### Post by ajgreeny on 2018-07-15
What does command ```
sudo apt update
sudo apt -f install -s
``` which is used to fix broken packages, show as output?  Let's see what that shows.

Depending on any errors you may be able to remove the **-s** option, which simulates the command's action without actually doing anything, in order to run it.

If that does not help we may need to delve a bit deeper to see what is going on, for example, did you have any PPA repos enabled in 17.10 which may have created those dependency problems?

---

### Post by retrorelix on 2018-07-15
Running these commands gets the following output.
> 0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded

The 3 upgradable packages are libfarstream, libjavascriptcoregtk and libwebkit2gtk.

About PPAs, I really have no clue but its a possibility. Sorry for my lack of knowledge, I only use the Ubuntu PC for programming :(

---

### Post by ajgreeny on 2018-07-16
What about the **sudo apt update** command; surely you got much more output from that?

---

### Post by retrorelix on 2018-07-17
Here is the output:
> 
Hit:1[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
32 packages can be upgraded. Run 'apt list --upgradable' to see them.


---

### Post by ajgreeny on 2018-07-17
Now try running ```
sudo apt upgrade
```and show us the full output from that.

---

### Post by retrorelix on 2018-07-18
Here is the output:
[IMG]https://i.imgur.com/3Cwngy0.jpg[/IMG]
[IMG]https://i.imgur.com/lIerPQ9.jpg[/IMG]

---

### Post by retrorelix on 2018-07-22
I guess I just reinstall.

---

### Post by kazakore on 2018-07-22
I don't notice anything failed to upgrade.

What happens when you try:
```
startx
```

Which tty are you using?

---

### Post by retrorelix on 2018-07-22
> **kazakore said:**
> I don't notice anything failed to upgrade.

What happens when you try:
```
startx
```

Which tty are you using?

Using tty1. I get a messagebox saying: > Could not connect to session bus; /usr/bin/dbus-launch terminated abnormally without any error message.

---

