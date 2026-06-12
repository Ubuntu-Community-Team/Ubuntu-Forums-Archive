---
title: "GUI Root Privileges"
date: 2007-09-18
forum: General Help
---

### Post by Barakka on 2007-09-18
Hey there,

My brother installed Ubuntu (Feisty Fawn) on his laptop although he is used to Fedora Core 6 that we use on the desktop. He decided to install Ubuntu because it was said to detect a lot of hardware by itself, whereas Fedora Core requires manual configuration. Upon successful installation of Ubuntu, because the system had not asked him to define  a root password, my brother changed the root password, and stripped his everyday use account of administrator privileges. The situation now is that many options have disappeared from the menus, such as add/remove programs, Synaptic Package Manager, and various administration/preferences options. All he can do now is twirl his cube, unfold it, and jiggle his windows (oh, and Firefox and OpenOffice still work). Does anyone know how to get his admin privileges back?

Thanks

---

### Post by splintercellguy on 2007-09-18
Your brotherwould have done well to read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) . Basically, the root account is locked out by default, and administrative actions are done through sudo. While I believe setting a root account password shouldn't disable sudo, that's the way to utilize su.

---

### Post by Barakka on 2007-09-18
sudo isn't disabled. Perhaps I should have been clearer:

The account that ubuntu setup makes for you is given admin prviledges. While in it, he took off the check mark by "Administrator" beside his own name under "Users and Groups".

Is there a way to reverse this?

Much thanks

---

### Post by aysiu on 2007-09-18
This will help him recover admin privileges:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by HermanAB on 2007-09-18
Note that for graphical use in links from the desktop, use 'gksudo'.  That will pop up a dialog for the password.

Cheers,

Herman

---

### Post by Barakka on 2007-09-23
Thanks for all of your help, guys. I decided in the end to reload both OSes onto my hard drive once more (I dual-boot Ubuntu (Feisty) and Windows Vista). The problem is solved, and my laptop is working better than ever...except for the Windows part, which is still slow.

---

