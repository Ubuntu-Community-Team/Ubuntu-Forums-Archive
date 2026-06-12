---
title: "Ubuntu fails to boot, AND liveCD fails to see partitions to allow backup, 14.04"
date: 2014-11-19
forum: General Help
---

### Post by 3d4tPNm on 2014-11-19
So this is basically two problems in one

First: a few days ago Ubuntu 14.04 fails to load, I get to the boot loader, and if I choose Ubuntu 14.04, the screen goes black, with a flashing cursor on the top left, and freezes on that screen permanently. So that is my first problem, if that can be solved, it would be great.

So, I chose to use the LiveCD to use my computer, and it works, and I was able to access the hard drive partitions from the liveCD without problem. However, just yesterday the hard drive partitions ran into problems, well it simply couldn't detect the partitions properly. My computer is partitioned with a 25gb Linux boot partition, and a ~180gb ext4 partition (named "1"), which most of my files and data are on. However my computer once seems to detect a massive 247 gb partition. Which means I cannot use or back up the data.

[IMG]http://s29.postimg.org/k9sgs4qef/Screenshot_from_2014_11_19_16_17_11.png[/IMG]

As you can see from above, it does not detect my partitions correctly, and neither does Gparted.
Yeah, this computer is 7 years old and I'm surprised it is still running, barely, but I still need to back up my data before reinstalling Ubuntu, I don't want to take the risk of reinstalling, even though most of my data is on a separate partition from the boot partition.

---

### Post by oldfred on 2014-11-19
If system is that old it just may be hard drive failure. While you always should have good backup procedures as system gets older it becomes even more essential. 

From Live installer and Disks if newer version or Disk Utility with 12.04 what does Smart Data show?
If Disks click on drive and then tiny icon in upper right for additional options and then Smart data.

If drive is ok, then you may want to see if testdisk shows old partitions. And its deeper search may show files. If it does immediately copy them as you may not be able to later if you are having major issues.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by 3d4tPNm on 2014-11-19
The physical drive definitely seems okay, note the screen shot I took, I had to save it on the hard drive to take it. 

> From Live installer and Disks if newer version or Disk Utility with 12.04 what does Smart Data show?
If Disks click on drive and then tiny icon in upper right for additional options and then Smart data.

What do you mean by that? what is "Disk Utility with 12.04", and smart data? Also would the Gparted check function be safe to use?

---

### Post by oldfred on 2014-11-19
They changed the name of Disk Utility in 12.04 to Disks in 14.04.
But either has Smart data tools to check status of hard drive. Most hard drives have internal data that you can read to see if drive is failing. All I really know about Smart data is passing is good, anything else is a new drive.

[http://en.wikipedia.org/wiki/Smartmontools](http://en.wikipedia.org/wiki/Smartmontools)

---

### Post by 3d4tPNm on 2014-11-19
Hmm, yeah, I just tried using smartdata, and it returns "SELF-TEST FAILED"

---

### Post by oldfred on 2014-11-19
Not good.
That is why we suggest good backups all the time.

Did testdisk show anything.

You may be able to use photorec to try to work around the damaged areas and recover some data. I have used photorec, it takes forever, you have to have another drive with lots of room to copy data into. It only recovers files by type or its extension as tables with full file names are gone. Some files like mp3 or photos have internal data you can use to rename, but all others you have to manually rename. And if finds the delete copies as well as last saved so it you copied a file multiple times you have to sort thru them.

---

