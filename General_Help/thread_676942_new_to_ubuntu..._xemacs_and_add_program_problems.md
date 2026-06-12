---
title: "new to ubuntu... xemacs and add program problems"
date: 2008-01-24
forum: General Help
---

### Post by tsnax4 on 2008-01-24
Hi, I am new to linux and I am trying to install xemacs with out any luck.

I started by trying the add/remove programs but when I try to add xemacs it says "Emacs 22 (X11) cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

then when I tried in terminal this is what I get...

kyle@kyle-laptop:~$ The program 'emacs' can be found in the following packages:
 * emacs21-nox (You will have to enable component called 'universe')
 * emacs22-gtk
 * emacs22
 * emacs-snapshot (You will have to enable component called 'universe')
 * e3 (You will have to enable component called 'universe')
 * emacs-snapshot-nox (You will have to enable component called 'universe')
 * emacs21 (You will have to enable component called 'universe')
 * emacs22-nox
 * jove (You will have to enable component called 'universe')
 * emacs-snapshot-gtk (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>
[1]+  Exit 127                xemacs22
bash: emacs: command not found

[2]+  Exit 127                emacs
kyle@kyle-laptop:~$ sudo apt-get install emacs22
[sudo] password for kyle:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emacs22



If anyone could help that would be great, thanks I'm really lost

---

### Post by mali2297 on 2008-01-24
I suggest that you use the package manager Synaptic. From there, enable the **universe** repository (and others) through the menu **Settings > Repositories**. Then see if you can find the package **xemacs21** to install.

---

### Post by tsnax4 on 2008-01-25
thanks for the help, now if i could just get my windows to boot back up again along with ubuntu

---

