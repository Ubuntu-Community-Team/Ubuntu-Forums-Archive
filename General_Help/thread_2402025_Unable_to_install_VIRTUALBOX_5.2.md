---
title: "Unable to install VIRTUALBOX 5.2"
date: 2018-09-25
forum: General Help
---

### Post by drsnippers on 2018-09-25
Hi
I've tried to install  Virtualbox numerous ways with no success . I end up getting the following..

"drsnippers@drsnippers-LIFEBOOK-A512:~$ virtualbox

Command 'virtualbox' not found, but can be installed with:


sudo apt install virtualbox-qt


drsnippers@drsnippers-LIFEBOOK-A512:~$ sudo apt install virtualbox-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-5.2 needs to be reinstalled, but I can't find an archive for it.
drsnippers@drsnippers-LIFEBOOK-A512:~$ 
"
   .... PLEASE HELP!

---

### Post by timgood on 2018-09-25
Why not install direct from the VirtualBox website? This is what I always do and I have never had a problem. [https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")

---

### Post by ajgreeny on 2018-09-25
I also would recommend that you do what timgood says, but go one step further and follow the instructions in the section **Debian-based Linux distributions** at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) to enable the Oracle VBox repositories; in that way VBox will automatically be updated like everything else.

---

