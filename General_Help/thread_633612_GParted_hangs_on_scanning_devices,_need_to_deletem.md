---
title: "GParted hangs on scanning devices, need to delete/make new partitions"
date: 2007-12-06
forum: General Help
---

### Post by herbster on 2007-12-06
I have 2 partitions from my Feisty install that I would like to delete and use the space to make one. There's a 14gb /dev/sdb1 and 25 gb /dev/sdb2. Whenever I run GParted the doggone thing takes a good 10 minutes for "Scanning all devices..." and then when it's done, any time I hit Unmount on the partition it scans again, another 10 minutes or so and then it magically exits on its own. :confused:

I don't want to fudge anything up on my partitions so I thought I'd ask before going wild with parted or mke2fs :D

TIA!

---

### Post by ondre on 2007-12-14
I ran into the same problem and came across this just this morning
[http://gparted-forum.surf4.info/viewtopic.php?pid=3425](http://gparted-forum.surf4.info/viewtopic.php?pid=3425)

Seems as though having the floppy disk drive enabled in the BIOS would do it.  That explains it for me because I don't even have a floppy disk drive connected.

---

### Post by Keith Hedger on 2007-12-14
you can try downloading the supergrub disk (sorry cant remember where from google it) which has a couple of tools for partitioning etc or you can try fdisk in interactive mode ie fdisk /dev/YORDRIVETOPARTITION but be very careful with fdisk as you could hose your system, you will probably have to run it from a live cd.

---

### Post by herbster on 2007-12-14
ondre,

Thank you very much! I haven't tried the disabling of the floppy device in BIOS yet, though I will next time I need to reboot, however the fella's tip at the bottom of that thread you linked to worked like a charm. I just tried this:

```
sudo gparted /dev/sda
```

And GParted started up beautifully! Same with /dev/sdb. It reads both drives a-ok now. Thanks again!

---

### Post by victorllorens on 2008-02-25
For those who can't reboot:

Open a terminal and type: 
```
sudo apt-get install modconf
```

Modconf is a module manager and it plugs/unplugs modules in hot. Open it, in the terminal type:
```
sudo modconf
```
Then wrap to "kernel/drivers/block" option press enter, then wrap to "floppy" press enter and finally unplug this module.

Now you have no floopy and can run Gparted as always.

GL
Víctor Llorens

---

