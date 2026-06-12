---
title: "How to Maintain an installation?"
date: 2014-10-14
forum: General Help
---

### Post by UndeniablyRexer on 2014-10-14
I have a linux server that I like to play around with, install various server roles, applications, etc.  However, I'm having a hard time keeping the box clean.  I have stuff installed that I'm never going to use again, but I'm not sure how to cleanly get rid of it, especially when it was no installed with apt-get.

For example, I tried out Multicraft for a day, and I had to install a daemon along with PHP and MySQL.  I'm used to a Windows environment, is there anything similar to Add/Remove programs?

---

### Post by Lars Noodén on 2014-10-14
The tool to add or remove programs is apt-get or dpkg.  ;)  Installing any other way *will* make a mess.  If you are just playing around then maybe a virtual machine would be better.  You could do a fresh install and make a snapshot  of it.  Then roll back to that snapshot every time you want a clean start.  Otherwise your only option is the occasional full reinstall with formatting.

---

### Post by UndeniablyRexer on 2014-10-14
Hmm, well it's running a minecraft and ftp server full time, so virtualization and rollbacks don't really work:?, but If I'm just aware that things should be installed with apt-get then I can handle that :p.

---

### Post by Lars Noodén on 2014-10-14
Another option, on the occasion there is not already a package for the application you want to try, is to make your own package.  The first one or two times are hard, but then after that you know the method.  The advantage there is that you can uninstall easily.  The disadvantage is the first time at rolling your own package it is quite hard.  

Speaking of uninstalling, it is 2014 and there are very few use-cases remaining for [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  If you want secure file transfer then there is SFTP, and Nautilus and the other file managers have built-in SFTP support.  So there is no need for special client software.   It would make the net safer to [remove FTP](https://www.google.fi/search?q=stop+using+ftp), except in a few increasingly rare edge cases.

---

### Post by ian-weisser on 2014-10-14
I keep a journal on the machine. Can be just a text file.
Includes everything I install/remove that's not from the Ubuntu Repositories, and where I got it from.
Includes all applications I install from the Ubuntu Reposiotires (but not any dependencies, since those are automatic).
Includes all of my scripts and customizations and extra services, why I installed them, where they are located, and where I got them from.

Remembering exactly what I did (and why) is much easier that way.

---

