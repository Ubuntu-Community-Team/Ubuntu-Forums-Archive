---
title: "Nothing works anymore!!"
date: 2013-02-10
forum: General Help
---

### Post by ksaul on 2013-02-10
I was [remove wine..](http://ubuntuforums.org/showthread.php?p=12503071) and in the process I really ****** something up..

I was trying to remove the debootstrap environment, but i removed
> sudo apt-get --purge remove schroot

by accident... and now NOTHING - ABSOLUTELY NOTHING works.. Nothing will open from the Menu, when I try to run anything through terminal (even sudo apt-get), nothing can be found... HELP!!!

> 
ksaul@ksaul-EP45-DS3L:~$ sudo apt-get remove debootstrap
bash: /usr/bin/sudo: No such file or directory
ksaul@ksaul-EP45-DS3L:~$ whereis sudo
bash: /usr/bin/whereis: No such file or directory
ksaul@ksaul-EP45-DS3L:~$ /usr/bin/sudo


:'( :'( :'(

---

### Post by Bufeu on 2013-02-10
*"schroot* allows the user to run a command or a login shell in a chroot environment."
Without *schroot*, you can't run commands in a chroot environment. So, either run them as **sudo ***<command>*, or switch to root at the beginning by typing **su**.
```
apt-get install schroot
``` as root should fix it.

---

### Post by ibjsb4 on 2013-02-10
I assume you running from console.  Try installing **libc6**

---

### Post by ksaul on 2013-02-10
> **Bufeu said:**
> *"schroot* allows the user to run a command or a login shell in a chroot environment."
Without *schroot*, you can't run commands in a chroot environment. So, either run them as **sudo ***<command>*, or switch to root at the beginning by typing **su**.
```
apt-get install schroot
``` as root should fix it.

> 
ksaul@ksaul-EP45-DS3L:~$ apt-get
bash: /usr/bin/apt-get: No such file or directory
ksaul@ksaul-EP45-DS3L:~$ su
bash: /bin/su: No such file or directory
ksaul@ksaul-EP45-DS3L:/usr/bin$ root
bash: /usr/bin/python: No such file or directory


Nothing works.. software center included.. i cant even open a new terminal window

---

### Post by ksaul on 2013-02-10
Please someone help!!!

---

### Post by sandyd on 2013-02-10
libc6 [depends on schroot]("http://packages.ubuntu.com/quantal/schroot"), which essentially means you just removed most of the stuff on your system.

I suggest that at this point - backup and reinstall.

---

### Post by ksaul on 2013-02-10
> **sandyd said:**
> You still have dpkg on there?

If you don't, you are going to have to manually get the deb packages on another computer, extract the files, and manually install dpkg/apt-get/sudo all over again

yes dpkg is still installed, although same error applies when trying to run dpkg :(


when looking through File Manger.. /bin/su exists, but i can not run it through terminal?

a few more misc errors when trying to run programs in terminal
> 
ksaul@ksaul-EP45-DS3L:~$ cd ~
ksaul@ksaul-EP45-DS3L:~$ cd /var/
backups/ crash/   local/   mail/    spool/   webmin/  
cache/   games/   lock/    opt/     tmp/     www/     
chroot/  lib/     log/     run/     twonky/  
ksaul@ksaul-EP45-DS3L:~$ rm
bash: /bin/rm: No such file or directory
ksaul@ksaul-EP45-DS3L:~$ cd /var/log/
ksaul@ksaul-EP45-DS3L:/var/log$ firefox 
bash: /usr/bin/firefox: /bin/sh: bad interpreter: No such file or directory

---

### Post by ksaul on 2013-02-10
> **sandyd said:**
> libc6 [depends on schroot]("http://packages.ubuntu.com/quantal/schroot"), which essentially means you just removed most of the stuff on your system.

I suggest that at this point - backup and reinstall.

how can I make an ISO image of the filesystem at this point? im downloading ubuntu live CD right now


(from the live cd, is there a way to copy/install files onto a pre-existing filesystem?)

---

### Post by ksaul on 2013-02-10
is there a "rescue" method or anything to "repair" the ubuntu os from the installation CD? (im scared to death to reboot, and not beable to save my current data)

---

### Post by ibjsb4 on 2013-02-10
You should be able to use the live cd to access the hdd and save your files to maybe a flash drive(s).

Use the "try ubuntu" option on the live cd to access your hdd.

---

### Post by mc4man on 2013-02-11
> **sandyd said:**
> libc6 [depends on schroot]("http://packages.ubuntu.com/quantal/schroot"), which essentially means you just removed most of the stuff on your system.

I suggest that at this point - backup and reinstall.

Well with all the willy-nilly commands the Op has been running a fresh install & some future constraint do seem best avenue. 
As far as libc6 depending on schroot it's the other way around, schroot is just an 'accessory' package that's not default installed & can be safely removed if installed.

@ksaul - as far as what you orig. did, if you followed those instructions then you never installed any packaged version(s) of wine, you used make install. In that case you would have used _make uninstall_ from the proper prompt to remove your wine install(s). (bit of a moot point now

---

