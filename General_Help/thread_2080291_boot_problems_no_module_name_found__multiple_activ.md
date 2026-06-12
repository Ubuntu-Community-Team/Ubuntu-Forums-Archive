---
title: "boot problems: no module name found / multiple active partitions / missing partition"
date: 2012-11-03
forum: General Help
---

### Post by bishop_ on 2012-11-03
Hi all,

Recently I've been unable to boot to my Ubuntu OS.  I bought this Win7 PC a year and a half or so ago and immediately repartitioned it to make it dual boot win/linux, installing Ubuntu 10.04 on the new partition using an Ubuntu install disk (I'm pretty sure it was 10.04, but it could possibly have been 11 something I'm not 100% sure now).

The dual boot setup worked great for a year and a half up until about a month ago - I used Ubuntu for my work and Win7 for games - but then some Win7 program, I suspect the Microsoft Security Essentials antivirus thing but I'm not sure, suddenly overwrote the grub boot record or something and I started getting "no module name found" and was unable to boot the machine.

I burned a "super grub 2 disk" from my work machine and tried booting my dead home machine from that.  The grub 2 disk utilities were able to detect and boot windows, but not get me back to my ubuntu OS.  This was ok with me for the last month or so, as I was just playing games, so I didn't mess with it anymore.  But now I want to get back to my Ubuntu work environment.

Following the instructions on this post: [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/) I created a dedicated boot cd and ran the "recommended repair" utility.  This utility said it completed a repair successfully, but after that I started getting a new error, "multiple active partitions / reboot and select proper boot device".

Booting windows from the super grub 2 disk again I followed some online instructions on using windows' diskpart tool to select an active partition.  This lets me boot to windows without a CD, but I still can't find my Ubuntu OS anywhere.

Booting the dedicated boot cd again and running a diagnostic tool directed me to the following rather ominous-looking status readout:

[http://paste2.org/p/2423089](http://paste2.org/p/2423089)

It looks to me like it's saying the 300gb windows partition of my 500gb drive is detected just fine but the 200gb linux partition is no longer visible at all.  It's now just a mysterious block of 200 unreadable GB to the diagnostic tools.

Does this mean my linux partition got blown away somehow?  What could have done that?

Is it possible that the partition is still intact and there is some other tool I could use to detect it and boot to it again?

If the linux partition is destroyed, it is moderately, but not severely cataclysmic for me.  My data is backed up but there would be maybe 1~2 weeks of lost work, plus the several week hassle of reconfiguring my programming environment how I had it.

Please let me know if you have any ideas about what I should do.

Thanks,
Bishop

---

### Post by oldfred on 2012-11-03
you can see if testdisk shows old partitions.

repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by bishop_ on 2012-11-19
Thank you oldfred!  Running TestDisk 6.13 (the newer beta version kept freezing) from windows 7 fixed it.  I did a quick search for partitions from TestDisk and it found the Linux partition, then I selected "write", I guess to add the partition to the MBR or something?  It still didn't give me the grub dual-boot prompt after a regular reboot, but when I booted from my supergrub2disk it found the Ubuntu OS and let me boot to it.  Then I ran grub-install from Ubuntu and my machine was back to normal.  Thanks a lot!

---

### Post by oldfred on 2012-11-19
Glad that worked. 

Normally we run testdisk from Ubuntu liveCD or USB. Good to know it also works from Windows.

---

