---
title: "Clonzilla"
date: 2016-10-04
forum: General Help
---

### Post by daniell59 on 2016-10-04
Can I use clonezilla to clone a hard drive if the source hard drive is bigger than the target hard drive?
The partition on the source drive is smaller than the capacity of the target hard drive.

Thanks

---

### Post by howefield on 2016-10-04
With regards your first sentence, no, cloning a drive needs to be made to a drive of at least the same size.

With regards your second sentence, then yes, you could clone the source partition to the larger target hard drive.

---

### Post by QLee on 2016-10-04
daniell59
See if this solved thread on the forums helps you, or perhaps, suggests a different method that would achieve your goal:
[https://ubuntuforums.org/showthread.php?t=1891633](https://ubuntuforums.org/showthread.php?t=1891633)

---

### Post by kevdog on 2016-10-04
Clonezilla is a wonderful tool, and I've used it many times. Great if a boot partition dies or is corrupted.  Although I've been tempted to use it many many times, I have to always ask myself if I'm actually after recovering the partition itself -- or the data within the partition.  Most partitions are not completely full, so the amount of space they take up is far less than the partition space.  In some cases, if I've bought a new drive -- did I reinstall the OS on the new drive or do I want a clone of the old OS.  I'm finding more and more that when I experience problems, I usually want to reinstall the OS from scratch and then preserve the data within the user partitions.  Perhaps however this isn't what you want to do.

---

### Post by HermanAB on 2016-10-04
In my experience, Clonezilla is good for Windows systems, but almost always the wrong solution for a Linux system.

If you run Linux and your system goes south, what would you rather want: A restore with an old an tired version of Linux, or the latest and greatest system?  Also consider that restoring the old and tired system will take hours, while you can install a new system in about 30 minutes, then it should be clear that it is usually better to only back up your data.

---

### Post by bearlake on 2016-10-04
I'm with HermanAB as I only backup my /home directory and data keeping it to a separate partition.

I can do a fresh install in 15 min and point the new OS to my /home.

[Clonezilla]("http://clonezilla.org/clonezilla-live.php") and [Luckybackup]("https://www.linux.com/learn/easy-linux-backups-lucky-backup") works for me.

---

### Post by Mark Phelps on 2016-10-04
I have to disagree with Clonezilla taking HOURS.

I regularly use it, and it takes a little under 10 minutes to do a full image backup, but that is because I have included the step to verify the integrity of the backup image after it was created.

And, 5 minutes is the LONGEST it has ever taken to restore an entire system. 

Also, my systems are heavily customized, with apps and settings that are non-standard.  It takes a couple of hours to install a new OS version, add all the apps and configure all the settings.

So, I would rather spend a few minutes restoring from backup, than spend hours installing afresh.

---

### Post by HermanAB on 2016-10-04
Sounds like you need to look into Preseeding your install.

---

### Post by monkeybrain20122 on 2016-10-05
Use fsarchiver.It is in the repo and it can restore to a smaller partition as long as it is big enough for the content.[https://www.fsarchiver.org/QuickStart](https://www.fsarchiver.org/QuickStart)

It is very fast and you can clone your partitions live (while you are using the computer) , use the -a -A option for savefs

Also see [this thread]("https://ubuntuforums.org/showthread.php?t=2221842")

---

### Post by monkeybrain20122 on 2016-10-05
> **bearlake said:**
> I'm with HermanAB as I only backup my /home directory and data keeping it to a separate partition.

I can do a fresh install in 15 min and point the new OS to my /home.

[Clonezilla]("http://clonezilla.org/clonezilla-live.php") and [Luckybackup]("https://www.linux.com/learn/easy-linux-backups-lucky-backup") works for me.

I am with Mark Phelps, my system is heavily customised with a lot of compiled applications, it will take days if not hours to reinstall. My / partition is small (~ 20G and typically would be smaller for most people) and it takes 5 -10 minutes to clone with fsarchiver and less than 5 to restore. 

Moreover if it is a bad update a re-install will probably not do you any good, you want to restore to the latest good version. Backing up data is rather trivial if it takes a long time.

---

### Post by HermanAB on 2016-10-05
Also note that cloning assumes that the hardware is mostly the same on the cloned system.

If your computer went up in smoke and you  bought a new different one, then restoring the clone will be an exercise in frustration.

Installing a new system using Preseeding is better, since it can automagically install the newest Ubuntu with the newest device drivers.  If you need to replicate hundreds or thousands of computers, then Preseeding is also the best way to do it.

---

### Post by monkeybrain20122 on 2016-10-05
> **HermanAB said:**
> Also note that cloning assumes that the hardware is mostly the same on the cloned system.

If your computer went up in smoke and you  bought a new different one, then restoring the clone will be an exercise in frustration.

Installing a new system using Preseeding is better, since it can automagically install the newest Ubuntu with the newest device drivers.  If you need to replicate hundreds or thousands of computers, then Preseeding is also the best way to do it.

Cannot be further from the truth. I routinely use Fsarchiver to clone one system in one computer to create an identical one in another and the specs of the computers can be totally different. As long as there is no proprietary graphic driver it works. For Windows you may need the hardware to be similar, in Linux it is a lot more flexible (if there is proprietary driver then of course both computers have to have the same type of graphic cards)

Another thing I use it  for is system upgrade. I typical don't change my working OS for a new release until at least a month or two after release to make sure most bugs are ironed out. Instead I do a full, fresh install of the new OS in an external hard drive and take my time to tweak it to my liking and wait for bugs to be fixed, file some bug report etc. Then when it is ready I just clone it and restore it to my main machine. This way I get no unpleasant surprise, everything is tested and works as expected and got to keep all the customisations.

---

### Post by Kris_M on 2016-10-05
I have a 220gb SSD with win7 and Ubuntu 16.04.1  I routinely use Clonezilla to backup the linux partition and occasionally the whole drive (since I use/change win7 only rarely)  I find that I often screw up my linux build playing with mods and want to go back a few days. Easy! Voila!  I can test graphics drivers etc and can start with a clean system again very easily.  it takes me 5 min to restore an image where it would take me days to get a rebuild up to snuff with all the tiny system changes. And I consider my build to be basically vanilla.  I have a couple empty sata3 spindles lying around that I could easily grab if the whole SSD dies and I can't wait to run over to BB or MC to get a replacement.  I am lazy.  I have had catastrophic errors.  I plan ahead.  Yes I have off-site spindle backup images.

:D

---

