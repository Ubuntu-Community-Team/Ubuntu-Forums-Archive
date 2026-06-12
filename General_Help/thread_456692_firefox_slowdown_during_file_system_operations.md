---
title: "firefox slowdown during file system operations"
date: 2007-05-27
forum: General Help
---

### Post by flar on 2007-05-27
During file operations, firefox becomes unusable.  For example, if I empty the recycle bin or copy some large files, firefox freezes until the file operations are complete.  I'm using Feisty and did not have this problem on Dapper.  My hard drives are also set up properly, with DMA, etc. 

Anyone have this problem or know how I can fix it?

---

### Post by liberalist on 2007-05-29
I am new to linux, but I would say the problem is caused by the OS itself. I would advise you to install Epiphany (a web browser based on Mozilla) or Opera (a Norwegian browser, which is quite stable and fast), which are both really good. I hope there is another solution to your problem, though.

---

### Post by flar on 2007-06-03
I'm not just noticing it in firefox, the whole system seem choppy when there's a lot of disk activity.  It's behaving just like Windows.  

Anyone have any ideas?  Is feisty using a different I/O scheduler or something?

This choppiness is annoying.  I don't want to go back to Dapper!

---

### Post by flar on 2007-06-03
I had some time for a little research today.  I found that dapper used the anticipatory i/o scheduler, while feisty uses cfq.  I switched to the anticipatory scheduler on feisty and problem solved!

---

### Post by MindFork on 2007-06-04
Cool.  Please tell us noobs how you made the switch.

> **flar said:**
> I had some time for a little research today.  I found that dapper used the anticipatory i/o scheduler, while feisty uses cfq.  I switched to the anticipatory scheduler on feisty and problem solved!

---

### Post by flar on 2007-06-04
You have to edit /boot/grub/menu.lst

add 'elevator=as' at the end of the kernel line in grub, eg:

kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=/dev/hda1 ro quiet splash elevator=as      

"as" means anticipatory scheduler, other options are cfq (the default in feisty), noop, and deadline.  Read about them here:  [http://www.redhat.com/magazine/008jun05/features/schedulers/](http://www.redhat.com/magazine/008jun05/features/schedulers/)


A change like this should be considered carefully!  I'm sure there was a reason why the Ubuntu devs changed this option.

---

### Post by MindFork on 2007-06-04
Thanks for the info on that, flar.

I tried to duplicate the problem, but couldn't make it happen.  I copied over a couple of gigs worth of .avi  files from my windows box and all was well.  I then moved one to the trash and emptied it and nothing seemed slow or frozen.  

The box is a P4 3.0c with a gig of ram & 80 gig seagate sata hard drive.  Feisty fawn with a clean install (no dual boot)

So...I'm going to leave menu.lst alone

---

### Post by flar on 2007-06-06
^^yup, no need to mess with this if you don't have to.  It was probably something specific to my hardware, Athlon with 1gig RAM and two hard drives.  Could be the fact that I'm using two hard drives.

---

### Post by Crafty Kisses on 2007-06-06
> **flar said:**
> During file operations, firefox becomes unusable.  For example, if I empty the recycle bin or copy some large files, firefox freezes until the file operations are complete.  I'm using Feisty and did not have this problem on Dapper.  My hard drives are also set up properly, with DMA, etc. 

Anyone have this problem or know how I can fix it?

First you should see if anything is eating up resources and you can check this by going in terminal and typing:
```
top
```
Hope this helps. :)

---

