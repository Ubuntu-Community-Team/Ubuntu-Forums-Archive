---
title: "Ubuntu fails to boot"
date: 2018-11-14
forum: General Help
---

### Post by Hasimir on 2018-11-14
I just got a weird and disconcerting problem o_O
I was using my computer as usual, no problems.
During the day it downloaded some updates from the system updater, all normal, all as usual.
It asked me to reboot, but I did not do it until much later in the day.

When I rebooted, the system started... but it treated me like a sort of Guest. Trying to launch Opera, it told me I did not have admin privileges. It told me that Steam needed to update, but I had to launch it manually. Obviously when I tried to launch it manually, it simply seemed to do nothing. Same for all other programs I tried (Chrome, Firefox, VSCode).

So I tried rebooting it.
And now it doesn't boot up anymore... instead presenting me with this screen
[ATTACH=CONFIG]281631[/ATTACH]

What's happening?
What can I do? T_T

---

### Post by Bashing-om on 2018-11-14
Hasimir; Hello -

You have the advisory that indicates the file system is corrupt - "run a file system check manually" .

To that end you will need a liveUSB(DVD) .

Boot the liveUSB in 'try ubuntu' mode and provide us the out put of terminal command:
```

sudo fdisk -lu

```
so we confirm sdb6 as the target to direct fsck ( file system check ).

[INDENT][INDENT]so far
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2018-11-14
The first thing you need to do is what it says, run fsck on sdb6.
Are you mounting sdb6 in fstab? Is it / or /home?

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Hasimir on 2018-11-14
Thank you all for the super-fast replies! <3
I was in a real panic >_<

I did not have a liveCD/liveUSB at hand, but from the Windows partition I managed to find what amounts to a slightly clearer explanation of what the error message (and fix instructions) shown in the above picture.
I then managed to unmount the correct partition and to run fsck on it.
It asked me if I wanted to fix a bunch of problems.
I always said YES.
And then it booted fine, and I am now writing from my beloved Ubuntu partition ^_^

Again, thanks for the quick support!

---

### Post by Bashing-om on 2018-11-14
Hasimir; Great :)

You do good work .

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by Hasimir on 2018-11-23
UPDATE!

Apparently I suffer from the same problem every time I log into Ubuntu after I log in and out of my Windows10 partition.
The fix is always the same... easy and quick now that I know it.
But I would prefer to avoid the problem altogether.
Any ideas about what could be causing it?
Maybe a recent Win update?
Am I the only one with this problem?

---

### Post by oldfred on 2018-11-23
Windows does not see nor use Linux partitions?
Or did you add to Windows one of the drivers to read ext4?

Are you mounting the Windows partition with fstab or any NTFS partition.
Windows fast start up prevents normal mount and may cause issues.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by Hasimir on 2018-11-24
My setup is a clean Ubuntu 18.04 ... and then I created a partition to run Win10.
This has never given me problems before (or at least, not THIS problem).

The whole disk structure is:
Disk 1 contains the Linux partition, the Win10 partition, Grub and all the other partitions needed to make these systems work.
Disk 2 is all NTFS, logical, used as storage bz both Linux and Win10

Normally Win can't see Linux.

I just checked: FastBoot is OFF (but when ON it usually gives me different problems).

---

### Post by oldfred on 2018-11-24
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Hasimir on 2018-11-28
1) the problem happened also without the switch between Win10 and Linux. But I had the Linux system do some of its usual automatic software updates, and Ukuu also updated the kernel, and I run Steam (which is the ONE thing I do when I switch to Win10).

2) here is the log from running the Boot-Repair app. It says all should be fine. I'll report back here if the problem happens again :P
[http://paste.ubuntu.com/p/K93DjrsRSb/](http://paste.ubuntu.com/p/K93DjrsRSb/)

---

### Post by oldfred on 2018-11-28
Do not see anything really wrong.

You can delete old Manjaro entry in UEFI with efibootmgr.
man efibootmgr

You do have a newer kernel than standard in 18.04.1, did you install yourself or from ppa? That may have some issues.

Your drives are reversed. May not be critical, but Ubuntu install likes the ESP to be on sda. 
Drive order normally set by UEFI/BIOS. And normally from SATA port order. You probably have sda, installed to a lower SATA port number than sdb.

---

### Post by Hasimir on 2018-12-02
Thanks! :)

I've deleted the Manjaro entry using efibootmgr.

I regularly update the kernel using the Ukuu Kernel Update Utility.
Only stable, not-RC releases.

> 
Your drives are reversed. May not be critical, but Ubuntu install likes the ESP to be on sda. 
Drive order normally set by UEFI/BIOS. And normally from SATA port order. You probably have sda, installed to a lower SATA port number than sdb.


Not sure I understand what to do here >_>

---

### Post by oldfred on 2018-12-02
When you physically installed drives which SATA port did you use for each drive.
I try to start at SATA0 and go in order with DVD last or even last SATA port.
But motherboard manual and tiny numbers on ports often not easily seen or clear on which is which.

---

