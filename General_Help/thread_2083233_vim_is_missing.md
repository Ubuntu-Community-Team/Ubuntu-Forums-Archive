---
title: "vim is missing"
date: 2012-11-11
forum: General Help
---

### Post by eddyq on 2012-11-11
I downloaded a VMware image of ubuntu 12.04. But vim seems to be missing:

user@ubuntu:~$ vim
The program 'vim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>
user@ubuntu:~$ 

Then I tried yum install vim but got:
user@ubuntu:~$ sudo yum install vim
[sudo] password for user: 
Setting up Install Process
No package vim available.
Nothing to do
user@ubuntu:~$

So how do I install vim?

---

### Post by Vaphell on 2012-11-11
yum? as in .rpm based distros? ubuntu is not one (uses .deb).

what does **sudo apt-get install vim** do?

---

### Post by eddyq on 2012-11-12
Thanks, that did the trick. I'm new to ubuntu and was using yum in fedora.

---

