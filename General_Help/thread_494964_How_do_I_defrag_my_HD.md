---
title: "How do I defrag my HD?"
date: 2007-07-07
forum: General Help
---

### Post by AndyCat on 2007-07-07
Hello there. THanks in advance for the comments. I recently switched to Ubuntu, I had Vista before and I ended up hating it even more than before.
I have my ubuntu up and running just the way I want it but I've noticed or at least I haven't found andy application to defrag my HD or any other utilities like the ones I had in windows.
Can anyone tell me how to do it or what applications to use in order to keep my system running smoothly????


Thanks

---

### Post by Circus-Killer on 2007-07-07
in linux, you dont need to defrag the hdd. the hdd only starts fragmenting when its around 98% full. hence why there is no need for a defrag tool.

---

### Post by AndyCat on 2007-07-07
So no need to defrag?? OO-RAH!!!! how about scandisk or tuneup registry????

Sorry for my silly questions ;)

---

### Post by Circus-Killer on 2007-07-07
linux doesnt have a registry, and dont worry about scandisk for now. while you're still new to ubuntu, the only thing you should concern yourself with in ubuntu is updates. whenever updates are available, use them. other than that you will be fine.
take time to get into ubuntu, and things will become clearer as time passes.
welcome to ubuntu and have fun with it. ;)

(one of the reasons why i use ubuntu on my laptops is the lack of maintenance)

---

### Post by AndyCat on 2007-07-07
Well thanks a lot buddy. These are the fastest answers I got, and they made me happy as my system has been doing it since I installed it.

Thanks again!!!!

---

### Post by Wiebelhaus on 2007-07-07
> **Circus-Killer said:**
> in linux, you dont need to defrag the hdd. the hdd only starts fragmenting when its around 98% full. hence why there is no need for a defrag tool.


lol ,one of the many reasons WHY I love it!

---

### Post by Topfs on 2007-07-07
Well you still need to Defrag NTFS partitions and Fat32 partitions right?

But I think Ubuntu do a scandisk every 30 boots or something. Mine did with Edgy and Dapper atleast

---

### Post by AndyCat on 2007-07-09
yeah plus its getting kind of annoying every 30 startups, is there any way I can set that option but lets say every 50 or 60 boot ups?:confused:

---

### Post by mcduck on 2007-07-10
> **AndyCat said:**
> yeah plus its getting kind of annoying every 30 startups, is there any way I can set that option but lets say every 50 or 60 boot ups?:confused:

For Ext2/Ext3 partitions the command to set boot count between running fsck is 'sudo tune2fs -c 75 /dev/sda1' (use any number you want, and of course use the correct partition..)

It can also be changed to use time-based system instead of counting the mounting times. This way you could configure fsck run once a month, for example..

See 'man tune2fs' for more info ;)

---

### Post by AndyCat on 2007-07-10
thanks it work now how i want it:)

---

### Post by bodhi.zazen on 2007-07-10
DO NOT RUN FSCK ON A MOUNTED PARTITION !!!!

If you do not understand that, well, do nothing, let Ubuntu take care of everything, your partition will be checked from time to time automatically.

This is a big difference with windows ;) you run fsck either from a live CD or as part of the boot process (before the partition is mounted).

---

### Post by AndyCat on 2007-07-10
Ok I wont do it but if I use that command to set the check up every 60 times and then restart my ubuntu what is gonna happen?? or could you be more precise in how am i supposed to do it?

Thanks in advance:confused:

---

### Post by tuxlinux on 2007-08-05
Perhaps this article will explain thoroughly why we don't need to defrag Linux.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by MarkusRTK on 2007-08-06
I don't think AndyCat got an answer to his question, so--

You can definitely use that command mentioned earlier, all it'll do is set the frequency that your computer scans itself (every 60 mounts by your suggestion). (Also make sure you point it to the right drive -- might be dev/hda1 rather than sda1, or even hda2/sda2 if you're partitioned.) 

So when you get to that 60th boot, on startup your computer will do a scan -- just like it does now every 30 boots. And, so you know, this has to be at boot time, so it can happen before the disk is mounted. (Like Bodhi said, if you fsck a mounted drive, chaos results; but you have to try fairly hard to make that happen.)  That's all there is to it, no worries.

Also, a tip: there's a command you can use to make it scan on your next reboot, if for some reason you're worried about your filesystem integrity (say, you've been crashing a lot, or getting unpredictable errors). Just enter a terminal and type

```
sudo touch /forcefsck
```

and then on your next boot you'll get a scan. (Helpfully, that scan also resets the fsck counter back to zero.) I suggest creating a launcher for that and sticking it in your Main Menu somewhere, but that's up to you.

HTH

---

