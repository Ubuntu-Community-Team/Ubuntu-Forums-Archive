---
title: "Ubuntu 12.04 Update Manager error"
date: 2014-04-09
forum: General Help
---

### Post by travisrector1995 on 2014-04-09
Every time I open the Update Manager, I keep getting this error:
(Please disregard my bad editing skills, lol)
[IMG]http://oi60.tinypic.com/wa3y4y.jpg[/IMG]
I recently installed Maxthon as my main browser, and it's working perfectly, as I'm using it right now. Would re-installing it help? Thanks for the help. This error is preventing all other updates I may have. It will search for updates, then show this error, and the only option I have is to close it.

---

### Post by mansonfan78 on 2014-04-09
Did you install Maxthon from a ppa?

---

### Post by travisrector1995 on 2014-04-09
> **mansonfan78 said:**
> Did you install Maxthon from a ppa?
I'm guessing not, because I downloaded it from Maxthon's website, and installed it with Gdebi Package Installer. I had to install another package, which it then re-installed Maxthon by itself. That fixed the error I received and now shows updates, but now has a different error. 
[ATTACH=CONFIG]251884[/ATTACH]
It doesn't say anything about Maxthon anymore. Just don't know what this means. Thanks

---

### Post by mansonfan78 on 2014-04-09
I'm guessing the installer added a ppa to your software sources so that it could be updated.  Check your software sources and disable any ppa related to Maxthon and then check for updates again and see if you still get any error messages.

---

### Post by plucky on 2014-04-10
> **travisrector1995 said:**
> I'm guessing not, because I downloaded it from Maxthon's website, and installed it with Gdebi Package Installer. I had to install another package, which it then re-installed Maxthon by itself. That fixed the error I received and now shows updates, but now has a different error. 
[ATTACH=CONFIG]251884[/ATTACH]
It doesn't say anything about Maxthon anymore. Just don't know what this means. Thanks

Open a terminal (Ctrl+Alt+t) and run ```
sudo apt-get update
sudo apt-get dist-upgrade
``` and post output if any errors.

Be careful with partial upgrades,make sure you look at what it trying to install and upgrade.

Good Luck

---

### Post by travisrector1995 on 2014-04-10
> **mansonfan78 said:**
> I'm guessing the installer added a ppa to your software sources so that it could be updated. Check your software sources and disable any ppa related to Maxthon and then check for updates again and see if you still get any error messages.
> **plucky said:**
> Open a terminal (Ctrl+Alt+t) and run ```
sudo apt-get update
sudo apt-get dist-upgrade
``` and post output if any errors.

Be careful with partial upgrades,make sure you look at what it trying to install and upgrade.

Good Luck
I've found out the problem. Maxthon was the issue for the first error, but the partial upgrade error was due to this ppa:
[http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu)
I don't know why that ppa was on there and I don't even know what it is. But after I unchecked that, it didn't show the error. 
Thanks everyone for their help!! I'm glad to get these issues fixed.

---

