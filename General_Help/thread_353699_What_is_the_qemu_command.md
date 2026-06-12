---
title: "What is the qemu command?"
date: 2007-02-05
forum: General Help
---

### Post by closetpirate on 2007-02-05
What is the qemu command and what do I use it for? No man page available

---

### Post by ~LoKe on 2007-02-05
qemu is used to run virtual operating systems.  You'd use qemu to, say, install Windows or another distro within Linux.

[Here](http://en.wikipedia.org/wiki/QEMU).

---

### Post by closetpirate on 2007-02-05
anymore info that might help me understand what it does? I am trying to remaster a live cd and it requires the use of it

---

### Post by closetpirate on 2007-02-05
And how do I get it and install it

---

### Post by Rui Pais on 2007-02-05
use the search on top of the page wit a simple word 'qemu' ... look for all entries with howto ;)

[here is the simplest]("http://ubuntuforums.org/showthread.php?t=291935&highlight=qemu") (i think).

[An old one]("http://ubuntuforums.org/showthread.php?t=154265&highlight=qemu"), but very complete.

[here]("http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html") something outside forum.

[The main site for qemu]("http://fabrice.bellard.free.fr/qemu/").

---

### Post by 3rdalbum on 2007-02-05
Qemu is an emulator that allows you to run other operating systems within a window. Are you following a HOWTO? Because the HOWTOs recommend that you install Qemu to run your customised CD, but you don't need to do that.

```
sudo apt-get install qemu
```

That will install Qemu. From there, you can do man qemu to get all the information about how to use it.

---

### Post by lamego on 2007-02-05
QEMU is not required for the remastering, it is only required if you want to test you livecd image.
You can use QEMU or any other virtualization software like VMWare to boot from your image without actually burning it.

---

### Post by closetpirate on 2007-02-05
Well..... I don't know what VMware is either but I appreciate the links and help everyone I at least have a much better idea of what it is. I'll tell you what I am trying to do. I want to have a custom Knoppix CD to show off to my friends how great GNU/Linux stuff is. I not going to even try to show them something that isn't debian based because I don't know debian stuff let alone other distro's. 

I have two followup questions for everyone.

1. Do you have any suggestions of what I should include on my live CD stuff that doesn't require too much horsepower?

2. Do you have any other tutorial suggestions on remastering?

thanks for all your help

---

