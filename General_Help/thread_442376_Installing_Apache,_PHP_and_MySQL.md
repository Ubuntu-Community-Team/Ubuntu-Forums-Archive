---
title: "Installing Apache, PHP and MySQL"
date: 2007-05-13
forum: General Help
---

### Post by happysmileman on 2007-05-13
I'd like to set up Apache, PHP and MySql on my computer, I'm using Kubuntu 7.04.

If anyone has done this please could you explain how, none of the tutorials work, they all give errors (mostly MySql related), none of the tutorials for those errors work. So don't bother just posting to a tutorial

I'd preferably like PHP5, Apache2.2, and MySql5... But if these can't be gotten to work (which seems likely) I'd settle for something near as good.

---

### Post by happysmileman on 2007-05-13
Bump, and methinks since so many peopl seem to have this problem someone should make a (working) tutorial for Feisty

---

### Post by rturner on 2007-05-13
I don't know if you're just setting up a testing server on your LAN like I did, (and I hesitate to post a link to a tutorial), but [Xampp]("http://ubuntuforums.org/showthread.php?t=223410") worked for me.  

If you want something public, I wouldn't go that route.  If you do go with Xampp, I would uninstall other Apache/MySQL/PHP installs you have on your machine.  Xampp puts it all in /opt so you'll end up with duplicate installs and conflicts when you start Xampp.

---

