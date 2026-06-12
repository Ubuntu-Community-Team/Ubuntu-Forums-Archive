---
title: "IBus not working."
date: 2013-02-16
forum: General Help
---

### Post by 700 on 2013-02-16
IBus doesn't show up. I can use only Preferences window for Keyboard Input Methods. 
How to check what is wrong with my IBus?
Reboots are not helping. It is not even appearing on system bar, so how to fix it?

Conditions: 
- System: Ubuntu 11.10 / 64bit / AMD

---

### Post by thegod_slayer on 2013-02-16
hi,

did you try installing iBus at first cause it's not preinstalled in ubuntu 12.04

if not install iBus using this command

```
 sudo apt-get install ibus ibus-m17n m17n-db m17n-contrib ibus-gtk 
```restart then goto terminal goto ibus preference and then select your desired language.

---

### Post by 700 on 2013-02-16
I am using IBus for months. It just stopped working today.

---

### Post by thegod_slayer on 2013-02-16
try and update iBus to a newer version and then check if the problem persist

---

### Post by dino99 on 2013-02-16
also got an ibus issue recently here with RR i386

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944)

---

### Post by 700 on 2013-02-16
Once I update python on Ubuntu, so I don't want to make any more mistakes like that.
Please, leave an instruction how to safely update iBus to a newer version.

Conditions: 
- System: Ubuntu 11.10 / 64bit / AMD

---

### Post by dino99 on 2013-02-16
first step:
you might want to purge the ibus* packages, then reinstall them and see if then it work or not

second step:
if the above tweak have failed, then you can download the required packages from:
[https://launchpad.net/ubuntu/+source/ibus](https://launchpad.net/ubuntu/+source/ibus)

and install with : sudo dpkg -i  thatpackagenamei_want_2_install

---

### Post by 700 on 2013-02-16
My steps:

1.
~$ sudo apt-get purge ibus

2.
~$ sudo apt-get install ibus ibus-m17n m17n-db m17n-contrib ibus-gtk

RESULT:
The same - not working (only Preferences window for Keyboard Input Methods appears)

---

### Post by thegod_slayer on 2013-02-16
did it install correctly?

and a tip: when completely uninstalling a package provide a * at the end of the package
this * means all, so the purge command will remove all files installed under the name of the package

i think an easier way would be to complete removal and install of the package may solve your problem so repeat the steps provided by dino99

---

### Post by 700 on 2013-02-16
It started working after steps below:
3.
Input Method setup (from Preferences window for Keyboard Input Methods)
4.
~$ im-switch -s ibus

Thank you for help!

---

### Post by 700 on 2013-02-23
The same problem is back.
Do I really have to reinstall iBus each week?

---

