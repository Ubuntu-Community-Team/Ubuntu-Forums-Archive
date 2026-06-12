---
title: "permission denied TO INSTALL ANY GAME WHAT SO EVER"
date: 2007-10-14
forum: General Help
---

### Post by lowlux2gmail.com on 2007-10-14
what's the point of open source when everything is locked down harder the area51! 

i get permission denied for UT2004 and Wolfenstein: Enemy Territory

i have installed Enemy Territory over 100 times in every which way possible... i had to login to root to install it.. and its now locked. 

there suppose to install intro /usr/local/games but it needs root in order to do anything. 

i am using 7.04....

---

### Post by r-mo on 2007-10-14
For UT2004, Open a terminal

cd /media/cdrom
sudo ./linux-installer.sh

Works for me :)

---

### Post by Lord Illidan on 2007-10-14
> **lowlux2gmail.com said:**
> what's the point of open source when everything is locked down harder the area51! 

i get permission denied for UT2004 and Wolfenstein: Enemy Territory

i have installed Enemy Territory over 100 times in every which way possible... i had to login to root to install it.. and its now locked. 

there suppose to install intro /usr/local/games but it needs root in order to do anything. 

i am using 7.04....

Did you run the game from the installer? DON'T! Any files generated will then be given root permissions.

---

### Post by lowlux2gmail.com on 2007-10-14
> **r-mo said:**
> For UT2004, Open a terminal

cd /media/cdrom
sudo ./linux-installer.sh

Works for me :)


sudo: unable to execute ./linux-installer.sh: Permission denied


are game even allowed to be installed?

---

### Post by spupy on 2007-10-14
Some random thoughts:
- Your user doens't belong to the 'games' group?
- You run the script from a fat32 partition (or another partition from which you can't run executable files)?

---

### Post by r-mo on 2007-10-14
if the installer's on a hard disk try 
```
sudo chmod +x linux-installer.sh
```

The commands above worked fine for me on the official cd-rom though

---

### Post by -grubby on 2007-10-14
That's strange....You have permissions to pretty much do anything if you are root

---

### Post by spupy on 2007-10-14
> **nathangrubb said:**
> That's strange....You have permissions to pretty much do anything if you are root

Nope, i think. If I remember correctly, i couldn't run executable files from a fat32 partition even as root, since the partition itself didn't have the correct flag to allow file execution (or something like this, i can't recall good).

---

### Post by geirha on 2007-10-14
It's not an executable, it's a shell-script, so you don't need execute permissions. Just do ```
sudo bash linux-installer.sh
```

---

### Post by lowlux2gmail.com on 2007-10-14
UT2004 works.... CD KEY FILE IS LOCKED.

---

