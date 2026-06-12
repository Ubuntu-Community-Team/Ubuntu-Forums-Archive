---
title: "How to remove old kernels? Tried a few things already, not working"
date: 2013-03-05
forum: General Help
---

### Post by Heeter on 2013-03-05
Hi all,

Tried a few things already, but I cannot remove the old kernels from my ubuntu 12.10 64bit setup.

Tried the janitor through Ubuntu Tweak, tried Synaptic, and tried a few command line stuff I found on the internet. Tried fixing broken packages as well.

Is there a folder that I can just go in and manually remove these old kernels?

Thanks

Heeter

---

### Post by kclark on 2013-03-05
Have you tried this?
> sudo apt-get purge linux-image-x.x.x.x-generic 

sudo update-grub2


---

### Post by malspa on 2013-03-05
What happened when you tried Synaptic? That's how I always do it in Ubuntu. Or is there something different about 12.10 64-bit when it comes to removing old kernels that I'm not aware of?

---

### Post by mörgæs on 2013-03-05
There is very little benefit from removing an old kernel. If you compare the free space before and after you will notice that the change is minimal.

---

### Post by malspa on 2013-03-05
> **mörgæs said:**
> There is very little benefit from removing an old kernel. If you compare the free space before and after you will notice that the change is minimal.

Well, it can sure make for a tidier grub menu.

---

### Post by Heeter on 2013-03-05
> **malspa said:**
> Well, it can sure make for a tidier grub menu.

That is exactly what I am trying to achieve, LOL

Synaptic complains that I need to fix broken packages,

Heeter

This is what I am getting:
```

adminpc@linuxpc:~$ sudo apt-get purge linux-image-3.7.0.7-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.7.0-7-generic' for regex 'linux-image-3.7.0.7-generic'
Package 'linux-image-3.7.0-7-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adminpc@linuxpc:~$ 

```

Although Synaptic lists this particular kernel as a broken package.

Heeter

---

### Post by ajgreeny on 2013-03-05
In synaptic try using the menu item **Edit ->Fix Broken Packages**

---

### Post by Heeter on 2013-03-06
Hi ajgreeny,

Have tried that already, with no success


Heeter

---

