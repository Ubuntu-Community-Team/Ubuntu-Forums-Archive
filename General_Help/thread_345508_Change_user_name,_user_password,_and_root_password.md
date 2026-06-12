---
title: "Change user name, user password, and root password"
date: 2007-01-24
forum: General Help
---

### Post by iammeagain on 2007-01-24
I need to change the root password, the user password and user name because i have a computer at school installed with Ubuntu and they want it something certain.

---

### Post by Ramses de Norre on 2007-01-24
Run these as the user you want to change:```
usermod -l new_login_name
mv /home/old_user_name /home/new_user_name
passwd
sudo passwd root
```

---

### Post by ridgeland on 2007-01-26
Thank you.
I was only looking for how to change the root password.
sudo passwd root
worked.
I just installed Ubuntu.  In Fedora and SuSE I go to root in the terminal to do things like gedit and nautilus (with root priviledges)  I'm setting up /etc/fstab and menu.lst (grub.conf)
It strikes me as strange that my user ID can control root's password :confused:

---

### Post by smartbei on 2007-01-26
The sudo command runs the command that follows it with root permissions, just like a root terminal runs the commands with root permission. That is why you have to enter the root password when you use it.

---

### Post by ridgeland on 2007-02-17
:)  I'm liking Ubuntu and Xubuntu
The root password is of little value once you discover
$ sudo -i
to get to the good ol' root prompt #
This is very useful when you do a lot of mkdir, mount, gedit etc and get tired of sudo sudo sudo
Also I noticed in Xubuntu that you cannot add a printer without the root password, which is unknown!  so ...
$ sudo passwd root 
to give it a known value so you can add a printer.

---

### Post by Maestro23 on 2007-02-17
> **ridgeland said:**
> :)  I'm liking Ubuntu and Xubuntu
The root password is of little value once you discover
$ sudo -i
to get to the good ol' root prompt #
This is very useful when you do a lot of mkdir, mount, gedit etc and get tired of sudo sudo sudo
Also I noticed in Xubuntu that you cannot add a printer without the root password, which is unknown!  so ...
$ sudo passwd root 
to give it a known value so you can add a printer.

Hmm... I added my printer with my sudo password.

Whatever works for you though.:guitar:

---

### Post by ridgeland on 2007-02-19
Installing Xubuntu on a different PC (an old 200MHz Pentium) I found the same problem.
When I try to install a printer using the menu Applications -> Settings -> Printing I still cannot without a root password.  For newbees this is a problem.  For experienced users the next step of course is to find the command so you can run it from a terminal with $ sudo.  I could not find a way to see what the menu runs but with the Printing window running I checked $ top.  I found the command system-config-printer.  So running $ sudo system-config-printer I was able to add a printer without a root password.
Another issue to work around are installs.  I installed qtparted and the install put it on the menu.  But when I try to run it, it tells me I'm not root.  The work-around was to create a launcher in the panel (still Xubuntu) that runs "sudo qtparted".  I've had Xubuntu for a few days.  I hope to find how to edit the menus to add the "sudo" in such places.
I only make these comments in the hope that newbees always search before posting and might find it useful.

---

