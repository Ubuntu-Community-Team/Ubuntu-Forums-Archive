---
title: "Can`t reach partitions!!! How to recover my files?"
date: 2015-07-09
forum: General Help
---

### Post by noyanculum on 2015-07-09
Hi all,

Bad situation.. I don`t know what to do now. No tool can reach the partitions. Both Ubuntu and Vista are not booting now!! This is my workpc. I need to recover my files!

This is a dual os pc. Ubuntu 12.04 is installed alongside Vista. Ubuntu was at /dev/sda6/

I will write below the short of the long story:
- Ubuntu not booted and stuck at initramfs.

- I booted the pc with Live CD. Then I made "sudo fsck -b 32768 /dev/sda6".
-- I am asked a lot of "Free blocks count wrong for group #XXX". I told yes to all.
-- Then I tried reboot without Live CD.
-- Ubuntu not booted.

- I booted again with Live CD, I made "sudo fsck -b 32768 /dev/sda6" again.
-- I am asked a lot of "Free blocks count wrong for group #XXX". I told yes to all.
-- I tried reboot without Live CD. I booted again my pc.
-- Ubuntu itself(no live cd) automatically asked the same questions to me at the boot!! "Free blocks count wrong for group #XXX". I told yes to all.
-- Then Ubuntu not booted.
-- Now Vista neither can not boot!

"sudo fdisk -l" result: nothing listed.
"sudo gparted" result: Input/output error during read on /dev/sda
"sudo gpart /dev/sda" result: Fatal error: cannot get sector size on dev(/dev/sda).
"sudo testdisk": It shows a lot of read/write errors
"sudo sfdisk -l /dev/sda" result: read error on /dev/sda - cannot read sector 0
Disk Utility: It shows the hdd "Healthy".

What can I do to recover my data?

Thanks,
Rancs

---

### Post by Bucky Ball on 2015-07-09
> **noyanculum said:**
> 
I will write below the short of the long story:
- Ubuntu not booted and stuck at initramfs.



It would help if you could add the beginning of the story. What exactly had you done/ had happened prior to this? You did an update/upgrade? You installed some new app or software or were having issues and trying to fix the same? You switched the computer on one day and you were greeted with an error message or some other screen? What was the screen or error message?

It may be a hardware issue. How old is the disk you are trying to boot from? They all die eventually.

---

### Post by oldfred on 2015-07-09
Did you run the regular fsck before running the backup superblock. And did you then try any other superblock?

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5

---

### Post by noyanculum on 2015-07-09
Hi Bucky Ball,

Everything was working pretty good. Then yesterday morning Ubuntu is not booted. I updating it regularly. I think one of the latest updates caused a problem. Disk utility shows the hdd healthy.

Thanks

---

### Post by noyanculum on 2015-07-09
Hi oldfred,

Yes I tried the regular fsck first but it doesnt solve the issue. That`s why I tried fsck -b
After nothing helping, I tried also again superblock 0. It tried it in the 3rd or 4th try.

I booted the machine now with Live CD but it doesn`t see the partitions so I cant unmount something.

"sudo e2fsck -C0 -p -f -v /dev/sdb1" result: "No such file or directory while trying to open /dev/sdb1 Possibly non-existent device?"

---

### Post by noyanculum on 2015-07-09
Ok today should be my unlucky day :)

I opened disk utility and I started a self-test. When the test running without error messages, the electricity black out. Unlucky day :)))

Now again I have the electricty a few minutes later, I rebooted the pc with the Live CD. And surprisingly the file manager can see the partitions !!!

There is a partition named 104 GB Filesystem. I think this is /dev/sda6 (my Ubuntu partition). In this partition I see now there is a directory named "lost+found". When I double click on this dir, I get the error message: The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "lost+found".

There is also the swap partition on the list. When I click that, I can see the directoies and files of swap partition. But when I try to copy them to the usb stick, I get the error message: "Error splicing file: Input/output error"

There is also the Vista partition on the list. When I click that, I get the error message: "Error mounting: mount exited with exit code 13: Error reading bootsector: Input/output error". Then now this partition is disappeared from the list.

Now how I can recover my files of the Ubuntu and swap partitions?

---

### Post by noyanculum on 2015-07-09
Well I have a lot of backup files on the swap partition. I can see them now, but I can not copy themto the usb storage or to the desktop of Live CD. I get the error message "Error splicing file: Input/output error".

If I can copy at least these backup files, I will save my some important works. What can I do to copy these files? Any help would be greatly appreciated!

---

### Post by gordintoronto on 2015-07-10
The swap partition does not contain your data, your home partition does. Can you post the output of: sudo fdisk -l

---

### Post by noyanculum on 2015-07-13
Sorry I wrote a wrong sentence. I have a partition to swap files between Ubuntu and Vista. I meant this partition.

Anyway, I found out that the issue was the data cable of the harddisk. I changed it and everything is ok now.

Thanks.

---

