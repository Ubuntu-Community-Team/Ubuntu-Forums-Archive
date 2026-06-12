---
title: "Help: Partition and grub issue"
date: 2007-07-28
forum: General Help
---

### Post by LogeshP on 2007-07-28
I installed Sabayon linux on my HD the other day.   Its grub bootloader does not reflect Ubuntu as an option   So I wrote SuperGrub to a disk and got it to write Ubuntu back into the MBR.  Natuarally that wiped out any reference to Sabayon as an option which I'd like to keep.

I am now able to boot into Ubuntu (which works fine).  But it is a strange process.  I am dropped into a root console since apparently fsck failed to resolve UUID-3e...I'm told that Ctrl-D will resume the boot.  It does not.  I enter "reboot" and the boot continues as normal.

Question 1:  How do I fix the fsck problem so that it will boot directly in the normal way?

Question 2:  How do I give boot precedence back to Ubuntu's grub so that I can provide for the Sabayon option in menu.lst?

---

### Post by rillip on 2007-07-28
It shouldn't matter which grub it's using.  Just add an item to the menu.lst.  I'd suggest finding the other distro's menu.lst, copying it's entry, and pasting into Ubuntu's.

Typically a fair reboot resolves fsck issues.  If not, you could try running fsck manually.

---

### Post by confused57 on 2007-07-28
> **LogeshP said:**
> I installed Sabayon linux on my HD the other day.   Its grub bootloader does not reflect Ubuntu as an option   So I wrote SuperGrub to a disk and got it to write Ubuntu back into the MBR.  Natuarally that wiped out any reference to Sabayon as an option which I'd like to keep.

I am now able to boot into Ubuntu (which works fine).  But it is a strange process.  I am dropped into a root console since apparently fsck failed to resolve UUID-3e...I'm told that Ctrl-D will resume the boot.  It does not.  I enter "reboot" and the boot continues as normal.

Question 1:  How do I fix the fsck problem so that it will boot directly in the normal way?

Question 2:  How do I give boot precedence back to Ubuntu's grub so that I can provide for the Sabayon option in menu.lst?
Boot into Ubuntu, or use the Ubuntu live cd(if you cannot boot to Ubuntu), open a terminal(Applications---Accessories---Terminal), enter:
```
blkid
```
this will give the UUID's of your partition filesystems

Then check the UUID's in your /etc/fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

Compare the UUID's from the output of "blkid" and /etc/fstab...copy & paste the correct UUID from blkid into your /etc/fstab.   This should get Ubuntu booting properly.

Then to boot your Sabayon, determine the partition it's installed on:
```
sudo fdisk -l
```
the -l is a small "L"

Then you can add an entry to grub to boot Sabayon, using a configfile entry:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add a configfile entry at the very end of your menu.lst to boot Sabayon:
```
title        Sabayon
configfile   (hd0,5)/boot/grub/grub.conf
```

Substitute (hd0,5) for your Sabayon partition, e.g. (hd0,5) would be something like /dev/sda6
(hd0,4) = /dev/sda5
(hd0,3) = /dev/sda4
you get the picture

quit & save your changes.

Note:  If you use the Ubuntu live cd, you'll need to mount your root partition before you can edit /etc/fstab:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by LogeshP on 2007-07-28
Thanks for your quick replies.

Problem still persists.

As to q1: The UUID number was exactly the same.  Where is it getting the wrong UUID 3e.. from?

q2:  Althoghh  Sabayon comes up on the list,  I get an error that filename must be an absolute path or blocklist when I choose it and the boot stalls.

I'd appreciate any suggestions.

---

### Post by confused57 on 2007-07-28
> **LogeshP said:**
> Thanks for your quick replies.

Problem still persists.

As to q1: The UUID number was exactly the same.  Where is it getting the wrong UUID 3e.. from?

q2:  Althoghh  Sabayon comes up on the list,  I get an error that filename must be an absolute path or blocklist when I choose it and the boot stalls.

I'd appreciate any suggestions.

In the "blkid" command, there should be a UUID listed for each of your partitions, did all of them agree with the UUID's in your /etc/fstab...the UUID of the partition you installed Sabayon on probably changed and this is the UUID that you need to update...or you can just place a # in front of the UUID for your Sabayon partition in /etc/fstab, if you don't want it mounted at boot.

Please post the output of "fdisk -l" and the Sabayon configfile entry you added to your menu.lst.

---

### Post by LogeshP on 2007-07-28
Thanks Confused.  Commenting out the Sabayon partition solved the fsck problem;

here is the output from fdisk -l:-


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1540    12370018+   7  HPFS/NTFS
/dev/sda2            5100        9254    33375037+  83  Linux
/dev/sda3            9521        9729     1678792+   5  Extended
/dev/sda4            1541        3554    16177455   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda6            9521        9541      168619+  82  Linux swap / Solaris

Partition table entries are not in disk order

Here is my menu.lst entry for Sabayon:-

title           Sabayon Linux
configfile      (hd0,3) /boot/grub/grub.conf

Thanks.

---

### Post by confused57 on 2007-07-28
In your Sabayon entry:
```
title Sabayon Linux
configfile (hd0,3) /boot/grub/grub.conf
```
looks like you have a space between (hd0,3) & /boot/grub..., it should be:
```
title Sabayon Linux
configfile (hd0,3)/boot/grub/grub.conf
```

---

### Post by LogeshP on 2007-07-28
Wonderful, problem solved.  Many thanks, Confused.

---

### Post by confused57 on 2007-07-28
> **LogeshP said:**
> Wonderful, problem solved.  Many thanks, Confused.

Glad I was able to help...

---

