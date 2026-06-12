---
title: "Can I mount a partition as an .iso file?"
date: 2013-10-18
forum: General Help
---

### Post by Quaxo76 on 2013-10-18
Hi all, so I made this really stupid mistake when using unetbootin, and I started to wipe one of my data discs instead of a usb thumb drive.
I stopped it as soon as I realized the mistake, but now of course the partition is unreadable.
I don't have enough free space to make an actual .iso of the drive with dd (it's a 1TB drive) so to try to recover some data, I have to work on the actual drive.
I've had lots of success in the past with Isobuster running under wine; but it requires an iso file to work. So my question is: is it possible to mount the actual partition as an .iso file instead of as a directory? That way I could run isobuster and trick it into thinking it's working on a file, and I could check what data I need to save before re-formatting the partition. I tried with a simple "mount" command, but it complains that the destination is not a directory.

Or alternatively, is there other software that can scan the drive, show me a list of the recoverable files, and then let me choose what I want to recover? The softwares I've tried, always save every file they find, and as I said I don't have enough room to save everything - nor do I need to, as most things are already on DVD and it's way easier to just reinstall them. I just need to look at the files to find out what I hadn't backed up yet...

Thanks
Cristian

---

### Post by oldfred on 2013-10-19
You only overwrote the first 700MB or whatever size of ISO was. But vital data is in MBR. I might try testdisk as its deeper search may find files you can then copy. If not photorec does have options on what file extensions to recover. Does not speed up recovery as it has to scan entire drive but only copies files with those extensions.

       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

            Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

If you only had one partition you might be able to erase MBR as it has ISO data and convert it back to a hard drive MBR. Then manually write a new ext4 partition or whatever format it was. Then run fsck to try to recover data format. But I would try that only after others attempts have failed.

---

### Post by Quaxo76 on 2013-10-19
Thank you for your reply.
I haven't tries testdisk, I will as soon as possible.
Photorec I did try, and it's not good for me. It can recover files, and you can specify the file types to recover; but the problem is that there are many gigabytes of data, and I only need to recover a few files. For example, there may be 5000 jpeg files but I only need to recover those in a specific folder... and I don't have enough free space to recover everything. Or there may be some files I need to recover, but of which I've forgotten the extension. Basically, with photorec, you have to decide in advance what files it should recover; I instead need to see the list of recoverable files first, and then decide which ones to recover. That's exactly what isobuster does, that's why I wanted to mount the partition as an .iso file. I'm actually surprised it can't be done, since in Linux almost everything (hardware included) is handled as a file.

Anyway, I'll try testdisk tomorrow.

There was only one partition. I could try the fsck trick if everything else fails... how should I do to put a Hard Disk MBR in there?

---

### Post by oldfred on 2013-10-19
You can erase entire MBR. Last part of MBR is partition table.
 If you run this against the wrong drive you will have major issues.

   Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Backup the MBR e.g. Where X is your drive
sudo dd if=/dev/sdX of=mbr.bin bs=512 count=1

   Erase - Make double sure you have correct drive & partition
sudo dd if=/dev/sdX bs=512 count=1 | hexdump -C

Then see if testdisk sees partition table. 

Or else we can try guessing. parted can also do guessing semi-automatically.
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

This may be same with gui.
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

If partitioned recently then start sector is 2048, if older it may be 63. End sector should still be on drive for parted to find.

---

### Post by Quaxo76 on 2013-10-25
All my attempts to actually "revive" the partition have failed.
The files are still there though... I know because photorec can recover many of them. The problem is that I don't have enough free space to save them anywhere. That's why isobuster would be perfect for me, because it shows a tree with all the recoverable files, and only then you decide which ones to recover.
So, back to my original question, is there really no way to make a partition mounted (and accessible) as an .iso file?

---

