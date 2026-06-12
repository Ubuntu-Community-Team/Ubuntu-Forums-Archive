---
title: "A problem with GRUB after Windows update from 8.1 to 10 version"
date: 2016-08-02
forum: General Help
---

### Post by godsdog2 on 2016-08-02
I was trying to update Windows from 8.1 to 10 on my Dell Inspirion N5110 (Bios v. A11) with two OS installed: Windows 8.1, Ubuntu 16.04. Update haven't been successful and the following message appeared:

[I] error: no such partition
Entering rescue mode...
grub rescue>
[/I]
Then I have tried to boot from Ubuntu live-USB and use Boot-Repair tool with the default options. Unfortunately, it didn't help. The report produced by Boot-Report: [http://paste2.org/yw5YKK5w](http://paste2.org/yw5YKK5w)
Could you help me to solve the problem?

---

### Post by grahammechanical on 2016-08-02
Boot Repair fixed the Windows boot because it only finds Windows on that drive. Is Windows 10 loading? It is my guess that the upgrade to Windows 10 has re-written the hard drive partition table and ignored the Linux partitions. The Linux/Ubuntu partitions are still there. You need to repair the partition table. I do not know how to do that. May be Boot Repair can do that. I do not know.

I have my doubts about Windows 10 runing on a hard drive with an MBR partitioning scheme. I thought Windows 10 needed a drive with GPT partitioning scheme. But What do I know?

Regards.

---

### Post by godsdog2 on 2016-08-02
Boot Repair didn't change the situation. I see the same notification 

[I]error: no such partition
Entering rescue mode...
grub rescue>[/I]

and neither Win nor Ubuntu are available to boot.

---

### Post by yancek on 2016-08-02
I think grahammechanical is correct.  If you look at the fdisk output for sda and the start sector for sda4 (Extended partition) and the start sector for sda5, you can see there is a lot of space which in all likelihood your Ubuntu partition.  From what I have read, when windows does the update it rewrites the partition table and does not include the Linux partition.  I've seen a number of posts here with a similar problem.  I'm not sure this can be repaired with boot repair but I believe testdisk will work.  I'd suggest you go to their site and look for instructions while you are waiting for a response from someone who has used it.  The download link is on the left side of the page below and if you scroll down the page you will see a Step By Step tutorial.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2016-08-02
This is a well known & old bug with Windows. It has been in Windows reinstalls/updates to BIOS systems with Linux in a logical partition. It rewrites partition table without the Linux partition.
Many have restored missing partition table. Some even could just then boot, others did have to reinstall grub. Only a few have totally lost data.

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by godsdog2 on 2016-08-02
Thank you, guys!
Currently, I'm trying to use TestDisk utility. A warning rose:
[I]
Warning: the current number of heads per cylinder is 255 but the correct value may be 128.
 You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

[/I]I've decided not to change anything on this stage as it looks like all partitions were found.

---

### Post by oldfred on 2016-08-02
Best to backup current partition table.
Some have made incorrect settings in testdisk and lost even more partitions.
With backup you can at least restore to current configuration.

This is only for MBR, not gpt.
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by godsdog2 on 2016-08-07
Hi, guys

I have solved the problem with your help! My steps:

1) Boot from Ubuntu live-USB. 
2) Check the status of all partitions with GParted. A partition, where Ubuntu initially was installed, was presented as extended drive, like not formatted drive.
3) Run TestDisk with all predefined or TestDisk defined parameters. Just pressed Enter every time it asked.
4) The problem partition have changed its appearance in GParted after the first step have been completed. 
5) Run GParted again and now run 'Repair' (or something like that) on problem partition. Magic! All disks are healthy now! I can see files of my partitions!
6) Now run Boot-Repair from Ubuntu live-USB. 

That's all! Grub is repaired and allows me to choose OS. All partitions are repaired.

---

### Post by CraigThomas on 2016-10-01
For me, my problem was (I believe) caused by the Windows "Anniversary" update.  I was updating Windows 10 on my dual booting laptop (on which use Windows 10 about once a month) when after an extremely long download and install it rebooted.  But my Grub menu was missing and all I had was a black screen, with the same message as the OP.

I then spent a few hours reading up about the issue (which was not uncommon).  A few people mentioned the Anniversary update had caused this issue for them and for others said it had completely borked their computer.  It looked like to me I was just missing the Grub loader so I wasn't prepared to abandon all hope and re-install everything.  I did wonder how experienced or persistent some people were that went for a complete re-install - to a complete beginner I completely understand but hopefully an average linux user would try to fix it first.

Most people seemed to agree that the issue was that partitions were missing or mis-labelled (a little more serious than my first guess).  However I was able to fix the issue using the instructions here as a guide:
[https://ubuntuforums.org/showthread.php?t=1775331&page=3&p=10905969]("https://ubuntuforums.org/showthread.php?t=1775331&page=3&p=10905969")

I had 3 standard partitions, then another standard partition which should have contained two extended partitions.  So sda1 - 3 showed as NTFS partitions, sda4 showed as the standard partition holding my extended partitions, then I noticed sda5 (the swap partition) did not start at the same place as sda4 and did not use up all of the sda4 space (just the last part of it).  This indicated to me (from what I read) that I had a real sda5 extended partition "hiding" and the swap partition (shown as sda5) should have been sda6.

Here's what I did:

* Boot from Live Ubuntu USB (I presume a recent CD would also work)
* Took a look at the partitions using gparted (optional - just did so out of curiousity)
* From a terminal run
```
sudo fdisk -l
```
(To list the current partitions and sizes)
* Made a note of the location/size of the missing partition
* Run
```
sudo parted /dev/sda unit s print
```
(To start the parted command line app, looking at sda disk, using sectors for sizing, and output the list to screen)
* Within the parted app run the command
```
rescue
```
* Typed the start & end sectors (as noted earlier, I went for just below the expected start position and a little after the expected end position) to see if it finds partition
* When it found the ext4 partiton, I uncrossed my fingers and replied Y (yes) to recover the partition and put it back in the partition table.
* I typed "quit" to exit the parted app and "exit" to close the terminal then rebooted (remembering to remove the Live Ubuntu USB stick).
* Kissed the laptop when Grub re-appeared and then successfully tested both Windows and Ubuntu installs.

Problem solved for me :D
Hope this helps with yours!

---

