---
title: "How to unpack and install .Deb Packages?"
date: 2004-11-07
forum: General Help
---

### Post by mudbug007 on 2004-11-07
Hi Everyone,

I'm a newbie at Linux.  I've been trying to install K3b that's a Derban Package without any sucess.  I keep get a "Package not found" error.

The Command I use :  sudo apt-get install Filename.deb

Do I have to change the $PATH variable (which I don't know how to do) to point to the 
file?

Peace, love, and Ubuntu

---

### Post by ubuntu-geek on 2004-11-07
[QUOTE=mudbug007]Hi Everyone,

I'm a newbie at Linux.  I've been trying to install K3b that's a Derban Package without any sucess.  I keep get a "Package not found" error.

The Command I use :  sudo apt-get install Filename.deb

Do I have to change the $PATH variable (which I don't know how to do) to point to the 
file?

Peace, love, and Ubuntu[/QUOTE]
 to install a .deb package you can do:

> sudo dpkg -i file.deb

You can also install k3b via synaptic with universe enabled. To see how to enable universe you can look in the HOWTO section of the site its at the top :)

---

### Post by az on 2004-11-07
apt-get install k3b

This will install the latest version of k3b along with all its' dependancies in your database.

apt-cache show k3b 

to search the database.

If you have download k3b and it is in your current directory, dpkg -i k3b.deb will try to install the file, but unless you have all the dependancies installed, it will complian.  This is why apt is more advanced.  (Advanced Package Tool)

Use synaptic - It is a graphical frontend to apt.  It does all the downloading for you.

---

### Post by malikseun on 2008-05-07
please i have a problem, i just installed my first ubuntu OS. i want to install Oracle on it, i have done all the upgrades, and i want to install the oracle but it keeps replying that package not found... how do i locate the package or how do i unpack the package....please help

---

### Post by kerry_s on 2008-05-07
i don't see that in the repo's.
what is oracle?
do you have a link?

---

### Post by odysseusjak on 2008-05-07
For me, every .deb file is easily installed.  I just double-click on it and it launches an app and I click a button that installs the app.

---

