---
title: "Tux Shop install / alien rpm....?!?"
date: 2005-09-02
forum: General Help
---

### Post by orev on 2005-09-02
I don't seem to find a lot of information on the forum related to Tux Shop POS.

I tried to use alien to install the package.....but I don't seem to be able to start the application...or see if it really worked.

Any suggestions??

Heres what I've got in the terminal:

```
jason@HPDESKTOP:~$ sudo alien TuxShop-1.4-0.i586.rpm
Password:
tuxshop_1.4-1_i386.deb generated
jason@HPDESKTOP:~$ sudo dpkg -i tuxshop_1.4-1_i386.deb
Selecting previously deselected package tuxshop.
(Reading database ... 106997 files and directories currently installed.)
Unpacking tuxshop (from tuxshop_1.4-1_i386.deb) ...
Setting up tuxshop (1.4-1) ...
jason@HPDESKTOP:~$ tuxshop
bash: tuxshop: command not found
jason@HPDESKTOP:~$ sudo apt-get install tuxshop
Reading package lists... Done
Building dependency tree... Done
tuxshop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jason@HPDESKTOP:~$ tuxshop
bash: tuxshop: command not found
jason@HPDESKTOP:~$

```

---

