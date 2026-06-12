---
title: "Root disabled? I don't think so"
date: 2007-04-07
forum: General Help
---

### Post by jordilin on 2007-04-07
I've always thought that the root account was disabled in Ubuntu, but if I write:
```
sudo su
```
and I write my password I become root.
Anybody can explain what's going on? :confused:

---

### Post by Drate on 2007-04-07
It's the same as sudo -i.

There are obviously some things that one would need to do with Super User (root) privileges.  Well... things that some folks need to do.  Anyway, you can access a kind of "temporary" root login by typing "sudo su" or "sudo -i".  It cuts away the hassle of typing "sudo" in front of every administrative command you want to make, but it also makes you just that much more dangerous if you aren't sure what you are doing.  You may perform a command you think is harmless, not realizing it touches system sensitive files, but since you aren't prompted with a "permission denied" you'll never know... until your PC crashes. :-D

Personally I use it alot... I have even opened my file manager as root ("sudo -i" password, then "nautilus") because it makes my life just a little bit easier.

BTW:  You can completely enable the root account if you are really itching to live on the wild side. ;-)

---

### Post by cookfromfrozen on 2007-04-07
When people talk about the root account being disabled in Ubuntu, what they actually mean is that you cannot actually log in using the root account (either graphically or through a console). 

The example you posted (sudo su, sudo bash, sudo -i) lets you, as a non-root user, gain root privileges and start a bash shell.  This is different to logging in as root.

---

