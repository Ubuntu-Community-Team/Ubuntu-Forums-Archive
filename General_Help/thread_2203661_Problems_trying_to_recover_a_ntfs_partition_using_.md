---
title: "Problems trying to recover a ntfs partition using TestDisk"
date: 2014-02-04
forum: General Help
---

### Post by Clifor on 2014-02-04
Hi all,

First of all, sorry for my bad english (I'm spanish).

I am using lubuntu and I was trying to create an ext4 partition on my /dev/sdb (whose capacity is 500GB and it had two ntfs partitions of about 250 GB) using gnome-disks and I've lost one of my partitions.

I selected /dev/sdb disk and I saw it had 2.6MB of free space, so I created the new ext4 partition on that space. Immediatelly after clicking "OK", the second partition disappeared and the space that was occupied by it was assigned to the first partition. Then, I deleted the new partition I had just created, but it didn't solve the problem.

After searching on internet, I found TestDisk and followed the steps shown here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
The "Quick search" shows my old ntfs partitions and the new ext4 (despite I deleted it) and I can see that all the directories and files are still there, but on the next step it only shows the ext4, so I made a "Deeper search". After that, It found all the partitions but It told me something like "There is not enough disk space" and I couldn't do anymore.

I suppose that the 2.6MB of free space were not really free and contained the information about the partitions. The problem is that I can't tell TestDisk to ignore the ext4 partition and restore the partition table using only the two original ntfs partitions.

Could anybody help me, please?

Thanks.

---

### Post by varunendra on 2014-02-06
Welcome to the forums Clifor !

While it should be very easy to get your partitions back if you know what to do and how to do with testdisk, any mistake can make the situation more difficult.

So my first advice is to use the "P" option of testdisk to list your directories/files, and copy them to a different drive, preferably an external one.

Once you have your files backed up, either use the Left/Right arrow keys to change the EXT partition from whatever it is (*, P, L or E) to "D" (Deleted), and change the NTFS ones back to what they were (P or L), or if you are not sure, follow this guide to recognize what they are/were : [http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical](http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical)

Or, post back the entire screen text (or its screenshot) after it has finished Deeper Search. If posting the matter of that screen, make sure to wrap it within 'Code' tags while posting here. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by Clifor on 2014-02-18
Hi,

Sorry for the delay.  I haven't been at home last weeks.

I know how to use the "P" option to copy the files to an external disk  (I tried it with a 8 Gb usb stick and it worked), the problem was that I  didn't want to buy an external disk. Finally, a friend gave me a 320 Gb  hard disk he took away from an old laptop, but I still want to try to  restore the partitions without using it (I analized it before using it and TestDisk gave me the following warning: "The number of heads per cilinder is 255 but the correct value may be 16", so I think it is broken).

I've tryed to change the EXT partition to "D" (deleted), but TestDisk  doesn't allow me to do that.  I can only set it to "*" (primary  bootable; wich is the default state), "P" (primary) and "" (wich I don't  know what does it mean). The other partitions can't also be changed to  "D".

Here are some screenshots I took from TestDisk:

This is after selecting "Analyse":
[ATTACH=CONFIG]250473[/ATTACH]

After "Quick search", all the partitions are found:
[ATTACH=CONFIG]250472[/ATTACH]

But, after selecting "Continue", only the EXT partition is visible:
[ATTACH=CONFIG]250471[/ATTACH]

After performing a "Deeper search", appears the message "The hard disk seems too small!":
[ATTACH=CONFIG]250470[/ATTACH]



Thank you for your help.

---

### Post by coldraven on 2014-02-18
I have not used TestDisk for a long time but it did save my data once and I donated some money to the author.
Is this link any use? [http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
Scroll down to see **[SIZE=4][COLOR=#C0C0C0][B]Recovering an accidentally deleted NTFS partition** [/COLOR][/SIZE][/B]

---

### Post by varunendra on 2014-02-19
> **Clifor said:**
> (I analized it before using it and TestDisk gave me the following warning: "**[COLOR="#FF0000"]The number of heads per cilinder is 255 but the correct value may be 16[/COLOR]**", so I think it is broken).

This may be why testdisk couldn't detect the partitions or their size correctly. In the screen where you select the "[ Analyse ]" option, testdisk says this at the bottom -
> Note: **Correct disk geometry is required for a successful recovery**. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.

Accordingly, please try what it *thinks* may be a correct value. As far as I know, the changed value is only for its own usage for correct analysis. It is not written to disk until you choose to "**Write**" the partition table after analysis and verification (by yourself - that the partition structure is indeed what you want). So it is safe to experiment with different values (255, 240, 16 are the most common values).

In the same screen where you choose "[ Analyse ]", select the "[ Geometry ]" option > change the value of "Heads" to "**16**" > press 'Enter' > Ok > [ Analyse ] again.

Does it show the partitions/their sizes correctly this time? Does it let you change their type?

---

### Post by Clifor on 2014-02-19
The warning about the incorrect size of heads per cylinder is not about the disk I'm trying to recover but the disk that I want to copy the data to. Anyway, I'll try to change that value and to copy the data to that disk to see if it is damaged or not.

---

### Post by Clifor on 2014-02-19
Thank you, but this page doesn't say anything about the last message I get when I do a deeper search: "The hard disk seems too small!"

---

### Post by dragonfly41 on 2014-02-19
This might shed some light ...

[http://forum.cgsecurity.org/phpBB3/can-t-read-mft-t2726.html](http://forum.cgsecurity.org/phpBB3/can-t-read-mft-t2726.html)

---

### Post by varunendra on 2014-02-20
> **dragonfly41 said:**
> This might shed some light ...

[http://forum.cgsecurity.org/phpBB3/can-t-read-mft-t2726.html](http://forum.cgsecurity.org/phpBB3/can-t-read-mft-t2726.html)

Yup, their own forum should be a much better place for discussing in-depths of the program. We may not be able to help as much since we haven't experienced your situation, and it seems to be going beyond the basics now.

---

### Post by Clifor on 2014-02-21
Thank you for your help.
Finally, I copied all the data to an external disk, formatted the original disk and copied the data back to it again. That's not what I wanted to do, but I don't have enough time to investigate.

---

### Post by krishfrz on 2015-02-12
Hello,i accidently make my whole HDD unallocated hwile istalling ubuntu 14.04 after installing windows 8.1.then i know about the testdisk and try in ubuntu and successfully get back my windows 8.1 drive and games drive full with data.but i cant access the two drives one is softwares and second is multimedia(very important device have my family rare pictures) while i am in ubuntu i can able to see the software drive with name but cant access it and in windows it shows it as new volume which is of RAW type so i can't able to open it.Now how can i recover those partitions and one more thing is that my multimedia drive is of 283gb and after testdisk deep search it found partitions of same size and then i press enter it says "no partition found or select for recovery" then i qiut the testdisk and make the Whole process again and then i found only 3 same size partition and then again i press enter again it shows "no partition found or select for recovery".please i want to recover my drives and in windows 8.1 the 283GB partition is shows as free space.Please help i really want to recover them. [CENTER][COLOR=#000000]:cry: [/COLOR][COLOR=#000000]:cry:[/COLOR][/CENTER]

---

### Post by dragonfly41 on 2015-02-12
It is not a good idea to post a new question onto a "Solved" thread since your question might be missed. 

On your problem .. if you have access to another working PC I would first create a Ubuntu LiveUSB on a flash drive.

You will not see any Ubuntu content from Windows.

Boot up using your LiveUSB (read articles in this forum first) and click on TRY not INSTALL.

You might be able to view your files in Nautilus.

If your family rare pictures are to be protected then first clone your 284GB drive (using clonezilla on your LiveUSB) into another external drive at least the same size or more.

You can use this drive later as a backup drive so it is a necessary purchase. If you can't afford a purchase of a backup drive then you can still proceed with recovery but at the risk of losing your data (which should have been backed up in the first place).

If you are unable to access your files using LiveUSB then from the LiveUSB use testdisk and/or photorec which is part of testdisk installation.   Testdisk and photorec will ask you destination path to copy any recovered files.

---

