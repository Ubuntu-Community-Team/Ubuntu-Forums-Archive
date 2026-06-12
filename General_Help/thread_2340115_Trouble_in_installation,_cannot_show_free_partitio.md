---
title: "Trouble in installation, cannot show free partition."
date: 2016-10-15
forum: General Help
---

### Post by mullkun on 2016-10-15
I want to install ubuntu 16.04 alongside Win 8.1, so I followed the instruction online. I first made an unallocated partition and then turned off the secure boot in BIOS and fast boot. Then I burnt the image file into my USB. But the problem occurred in the section of installation type. It did not detect the partition I created before. 
And the error is Ubiquity crash in partman_dialog(). And it says the disk contains an unclean file system(0,0). I have no idea what this means.

Here is the problem:
[ATTACH=CONFIG]271635[/ATTACH][ATTACH=CONFIG]271636[/ATTACH][ATTACH=CONFIG]271637[/ATTACH]

The detail of the error is here(cannot upload the pic):

The disk contains an unclean file system(0,0)
Metadata kept in Windows cache, refused to mount.
Failed to mount 'dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown the Windows fully(no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.
mount: mounting /dev/sda1 on /cdrom failed: No such device.
blablablabla.......(same for the sad4 and sda5)

Can anyone tell me how to solve this problem? Thank you in advance. :)

---

### Post by &amp;KyT$0P# on 2016-10-15
What version of Ubuntu?

What happens if you try to look at the disk in Gparted?  and Disks (gnome-disks)?  and from Windows?

---

### Post by mullkun on 2016-10-16
I tried 16.10, 16.04 and 14.04. Same problem. 

What should I look for with these softwares?

---

### Post by &amp;KyT$0P# on 2016-10-16
Look for anything about the disk that does not match what you think it should be.  For example, check the partition table type and the partitions shown.  Gparted has View > Device Information and Partition > Information, both of which could be of help here.

**Do not make any changes to the disk at this stage.**  Just let us know the results, thanks.

---

### Post by oldfred on 2016-10-16
Did you also turn off Windows fast start up?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

You cannot create partitions in Windows for Linux.
Best to use Windows to shrink NTFS partition, but you must reboot so it can run chkdsk. 
Linux NTFS driver does not mount NTFS that is hibernated nor if it needs chkdsk.
If you want to create partitions in advance use gparted, or use Something Else to manually create partitions. 
Some of the auto install options LVM/encryption, or if Windows is not seen, you may erase entire hard drive.

---

### Post by mullkun on 2016-10-16
Yes I did, I also shrink the partition with Windows, then reboot. 
What is the difference between the partition shrink by windows and by Gparted? 
According to the instruction, I just shrink the partition, then the installer may detect the unallocated space.......

---

### Post by mullkun on 2016-10-16
I just check the partition on ubuntu installer(I suppose you want the Linux perspective), and the system first says "The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?", and I clicked cancel. 
Then it recognized almost the whole disk as unallocated partition. The /dev/sda is 465.76Gb, which is over 95% of my disk, and the device information is here:

Model: ATA HGST HTS725050A7
Size: 465.76 GiB
Path: /dev/sda

Partition table: unrecognized
Heads:255
Sectors/track:63
Cylinders: 60801
Totalsectors: 976773168
Sector size: 512

Here is what I got. Could you help me further?

---

### Post by oldfred on 2016-10-17
This is the only tool I know that will move backup gpt partition table from middle to end of drive where it is supposed to be.
to see if it sees drive:
sudo gdisk -l /dev/sda

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 


to have it make changes.
 gpt partition table in middle of drive
sudo gdisk /dev/sda
Command (? for help):
 launch gdisk, then type x, then type e, then type w to save your changes 


I think some vendors image drive using an image for a smaller drive. Then backup gpt is at end of smaller drive, but not really at end of larger drive.

---

