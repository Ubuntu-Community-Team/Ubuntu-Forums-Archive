---
title: "Bootup Sequence Documentation needed"
date: 2007-05-11
forum: General Help
---

### Post by doccpu on 2007-05-11
Where can I get a definitive answer to the boot up sequence for 6.06.1 server? In fact where can i get indepth documentation of debian/ubuntu  in general?

I need to know when and why the grubs screen resolution is reset to grainy mode by the system before it sets up the terminals. 
Or what log files are creted to show what it did and the results.

---

### Post by quark_77 on 2007-05-11
Hi doccpu,

I'm not sure I can answer all of your questions as I've the same questions myself really. I can tell you where to look at log files though. There are two options:
[LIST]
[*] dmesg. You can simply type dmesg at the terminal and it'll show you the kernel boot log. I use this:
```
dmesg | grep string
```
where string is what you're looking for. Put error in here to see kernel errors, vga for vga bits - once you have said documentation you'll know what to look for. You could pipe it to a file and search it:
```
dmesg > ~/kernel_log
```
which puts the kernel log in your home folder.
[*] the /var/log folder contains a number of logs, including kern.log (with .n being older versions, the higher n the older the version). You can search it using:
```
cat /var/log/kern.log | grep searchterm
```
[/LIST]

I hope this helps as a start!!

Quark_77

---

