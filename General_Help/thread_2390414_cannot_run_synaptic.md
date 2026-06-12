---
title: "cannot run synaptic"
date: 2018-04-28
forum: General Help
---

### Post by jgw on 2018-04-28
I tried to run synaptic and it tries and goes away.  I then tried to run it in a terminal:
greg@movies:~$ sudo synaptic
synaptic: error while loading shared libraries: libxapian.so.22: cannot open shared object file: No such file or directory

greg@movies:~$ sudo apt-get install libxapian22v5  (I tried to install without the 'v5' but was told it wasn't available)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxapian22v5 is already the newest version (1.2.22-2).

I also removed synaptic and then installed synaptic and got exactly the same results.

I was rooting around and found a cleaner called: Ubuntu Cleaner.  I read about this one and it seemed safe so I ran it.  Now, I fear I have serious problem.

Anybody have any thoughts on this one?

Thank you.......................

---

### Post by Yellow Pasque on 2018-04-28
Try to reinstall the package in question:
```
sudo apt-get install --reinstall libxapian22v5
```

Also, you shouldn't be starting GUI apps with sudo: [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
Try:
```
synaptic-pkexec
```

---

### Post by jgw on 2018-04-28
Thank you for the reply

I suspect that the problem is the 'v5' at the end but I will try your suggestion.

I usually run gui stiff with a 'gksu' but got lazy

Thanks again!

---

### Post by Frogs Hair on 2018-04-28
What Ubuntu version and desktop ? Gksu has been depreciated and is no longer used in 18.04. The following is a safe alternative to sudo also: ```
sudo -H synaptic 
``` If using the Wayland session in 17.10 or 18.04 try logging into the Xorg session.

---

### Post by jgw on 2018-04-28
using ubuntu 16.04.4

Thanks for the reply!

---

### Post by jgw on 2018-04-29
Temüjin;
I did as you suggested and it worked!

How is synaptic-pkexec different from just plain synaptic?  (I ran synaptic-pkexec, synaptic in terminal and just called it from my desktop and it worked in every instance!  I think the re-installation did the trick.

Thank you!

---

### Post by Yellow Pasque on 2018-04-29
You can read about some of the technical details here:
[https://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo](https://askubuntu.com/questions/78352/when-to-use-pkexec-vs-gksu-gksudo)

---

