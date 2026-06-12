---
title: "Partition Tragic, Copying my ubuntu to a spare partition"
date: 2008-02-24
forum: General Help
---

### Post by Gazza-spins on 2008-02-24
Hi there!
I've been playing around with Ubuntu (gutsy) for about a week now, when i installed it, i installed it to a spare 20gb IDE HDD i had sitting in my pc, however, this has proven to be quite the bottle neck on performance, but in my pc i have a 300gb Sata2 drive, which has a 20GB partition on it which i _used_ for Vista [note the past tence] 

 I'm wondering if using say partition magic i could move the Ubuntu IDE install to the spare 20GB partition on the 300GB SATA without causing damage to any of the installs.

I wouldn't mind re-installing Ubuntu to this partition, but, the main reason I used the IDE drive was to avoid Ubuntu screwing with my flawless windows install where all my precious files are The whole partitioning tool at install scares me, also, I've put allot of work into getting my Ubuntu to a working usable state.

The Good thing about my current set-up is when i turn my computer on, i can hit f11, and select whether i want to boot from the IDE (ubuntu) or the Sata (windows) so no  fights for domination.
    I'd imagine if i were to successfully copy i would have issues selecting which i wanted to boot with.

I'm not yet ready to make the full move to Ubuntu, strictly because of the Gaming performance, and the lack of functional Drivers for my X-fi.

am i on the right track? or should i just take the risk and install Ubuntu to the Partition and put up with a MBR fight and possible complete loss of two working OS's, or just not fix whats not broken

---

### Post by lswest on 2008-02-24
what you could do is make an archived backup of your current system, install gutsy on the 20GB partition, update it, and untar the backup, which would effectively restore your system.  have a look at [http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)   also, if you've been running that gutsy on the same PC, there shouldn't be a problem, but if it's a different PC you've been running it on, it may run into a few problems with drivers and such.  good luck

*EDIT* and you'll also have to install GRUB into the MBR of the sata drive in your PC

---

### Post by Gazza-spins on 2008-02-24
Grub, that's a part that scares me, because it means if I stuff it up I could loose everything. Thanks for the suggestion and speedy response! i'll make a backup regardless (I've just about kocked it up a couple of times)

---

### Post by lswest on 2008-02-24
yeah, i prefer to avoid playing around with GRUB too, but when you install Gutsy into the 20GB drive it should automatically install GRUB into the MBR, which should automatically add entries for windows, sorry i forgot about the fact it would be installed onto the drive :P lack of sleep XD

---

### Post by Gazza-spins on 2008-02-24
yeah, Grubs present on the 20gb IDE, but not the 300GB SATA (which contains a 20GB partition with nothing on it)

It's probably not your lack of sleep, it's probably my lack of a decent explanation.

Having it set up like this offers me protection from loosing information, at the cost of performance. 

a 20GB 5400 IDE is no match for a Sata drive :D

---

### Post by lswest on 2008-02-25
sorry, my bad this time :P i meant when you install Ubuntu on to the sata drive (i meant partition in the last post, not drive :P), it will automatically install GRUB into the MBR, and (should) add entries for your Windows OS into the menu, so you can choose which OS you want to boot.

---

