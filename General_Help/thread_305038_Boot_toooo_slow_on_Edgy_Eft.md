---
title: "Boot toooo slow on Edgy Eft"
date: 2006-11-22
forum: General Help
---

### Post by LedStyle on 2006-11-22
Hi...

I just installed Ubuntu Edgy Eft 6.10 on a PC with 2 SATA hds (Ubuntu is in a sata HD), 1 IDE HD and 1 CD.

But the boot is too slow.


Look the graphic to understand the problem:

[[IMG]http://img453.imageshack.us/img453/5210/crazyed4.th.png[/IMG]](http://img453.imageshack.us/my.php?image=crazyed4.png)

I tried a "dpkg-reconfigure" on udev and volumeid bot nothing... :(

Can someone help?

---

### Post by doobit on 2006-11-22
There have been a number of complaints like this. I have a much slower computer (AMD Athlon 800 with a 13GB 5400RPM drive) and mine boots up in about 40 seconds. I am using the 2.6.18.1 SMP kernel and I ran profile in grub after I compiled the kernel.
How do I analyze it and make a graph like the one you did?

---

### Post by iamhugeinjapan on 2006-11-22
To get the graphs you need to install a program called bootchart

```
sudo apt-get install bootchart
```

It runs automatically every time you boot (until you remove it) and puts the graph in /var/log/bootchart. It doesn't work with all configurations but give it a shot.

---

