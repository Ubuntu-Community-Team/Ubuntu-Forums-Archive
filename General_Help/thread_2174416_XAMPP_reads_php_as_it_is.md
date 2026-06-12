---
title: "XAMPP reads php as it is"
date: 2013-09-14
forum: General Help
---

### Post by kier2 on 2013-09-14
*solved.*

---

### Post by Lars Noodén on 2013-09-14
You might consider winding back a few steps and using LAMP instead.  There is an easy way to install it in Ubuntu.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Mind that you include the caret. 

Doing it the LAMP way offers several advantages.  First, it provides automatic updates of all components.  That includes both security and maintenance updates as well as any version upgrades that might come along.  Second, it puts things in standard locations.  That means, among other things, that you can follow the many Ubuntu-oriented guides around the net and that you can more easily get help from people should you need  it.  XAMPP puts things in non-standard locations and even makes double copies of things like Perl, which is already found on your system.  Plus you will have to not only update manually, you will have to track the versions manually to know when they are ready for updating.  It will definitely make things easier to troubleshoot if you use LAMP.  

XAMP is not needed on Ubuntu, you have LAMP.  It might have been fine on a Windows machine where it is difficult to install software, but there are much more advantages instead in doing things the Linux way when on a Linux machine.  All around, LAMP will save you a lot of work and trouble compared to XAMP.

---

