---
title: "[SOLVED] Feisty and Gnome File Browser"
date: 2007-07-06
forum: General Help
---

### Post by senken12 on 2007-07-06
After my update to Feisty Fawn on my Toshiba Satellite Pro A100 - I have not been able to use the File Browser at all.
When I open it - the files do not appear and when I try to close it - It comes up with the "Force Quit / Wait" option.

And sometimes when I click "Force Quit", it feels eligible to attempt to open again.
This then occurs for several attempts and never works.

---

### Post by yopnono on 2007-07-06
try to open the file browser in the terminal, so you can see the errors.

---

### Post by az on 2007-07-06
> **yopnono said:**
> try to open the file browser in the terminal, so you can see the errors.

The command is:

nautilus


As well, what happens when you run

sudo apt-get -f install

(That would fix any half-installed packages)

---

### Post by senken12 on 2007-07-13
> **yopnono said:**
> try to open the file browser in the terminal, so you can see the errors.

Did that,
Same thing happened like how I opened it before... Nothing came up in terminal.

senken@senken-laptop:~$ nautilus
senken@senken-laptop:~$ 

That came up ^

---

### Post by senken12 on 2007-07-13
> **az said:**
> The command is:

nautilus


As well, what happens when you run

sudo apt-get -f install

(That would fix any half-installed packages)


This came up:

senken@senken-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic libdbus-1-2 libgnutls12 libtasn1-2
  libxine-main1 linux-headers-2.6.20-15 libxvmc1 libmodplug0c2 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
senken@senken-laptop:~$


Problem still there

---

### Post by yopnono on 2007-07-13
try sudo aptitude install nautilus or sudo aptitude reinstall nautilus

---

### Post by az on 2007-07-13
All your packages are properly installed, so let's assume that your problem is in your personal configurations.  Go to System - Administration - Users and Groups and create another user.  Give that user Admin privs and log out.  Log back in as that new user.  Try to reproduce your problem.

---

### Post by senken12 on 2007-07-17
> **az said:**
> All your packages are properly installed, so let's assume that your problem is in your personal configurations.  Go to System - Administration - Users and Groups and create another user.  Give that user Admin privs and log out.  Log back in as that new user.  Try to reproduce your problem.

Okay, I did that and there wasn't any problems whatsoever...
Whenever I do it on my normal username, it freezes whenever I try and access "Home Folder" "Desktop" but not "Computer" or "Trash"... So it's only my user's area which freezes it...

---

