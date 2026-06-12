---
title: "Broke boot order"
date: 2014-10-07
forum: General Help
---

### Post by masstumor29 on 2014-10-07
I'm running the latest Ubuntu, I have three partitions on my hdd. 128gb ntfs, 4gb ntfs and 134gb used for Ubuntu. I formatted my 4gb partition using gparted and set the flag to boot. I then moved the contents of my windows seven iso to this partition.

I forgot a step and it kept booting into windows installation but it did not recognize my 128gb partition. Now when I start my computer I'm greeted with a nice annoying error to insert a windows installation disk.

I want my ubuntu partition back. It is not over written, its untouched by all this. The problem is I do not have access to any disks or usb drives to make a bootable img. I have a old outdated Kali linux disk that I can get into busybox with.  That's it, This disk does not allow me to install because it is one that had the old bug that returned all archives invalid.

My question is can I repair the boot using busybox and set the boot flag to the correct partition?

---

### Post by yancek on 2014-10-07
Were you booting both windows and Ubuntu with the windows bootloader prior to re-formatting this partition?  If so, what was on that partition?  Did it contain the boot files for windows?  If you were booting both with the Ubuntu Grub bootloader, I don't see how the action you report could cause what you indicate is happening.  The boot files for Grub have a small part in the mbr and the rest are on the ubuntu partition so re-formatting a totally separate partition would have no effect.  Do you have only one harddrive?

---

### Post by masstumor29 on 2014-10-07
No that computer has only the one hard drive, also I was not dual booting. I was just running straight ubuntu. I formatted the 4gb partition and changed the flag to boot onto that partition. As mentioned I forgot to copy something to that partition before restart. 

It would boot the windows install but couldn't locate any harddrives to install. I figured I would try the boot repair using the disk and see if it would force install to recognize the 128gb partition. Instead it greeted me  with the insert windows installation disk. 

My linux partition is still intact and untouched just the boot flag was changed.

---

### Post by oldfred on 2014-10-07
Boot flag has nothing to do with Ubuntu booting. Grub does not use boot flag. 

But Windows has to have a boot flag on the NTFS primary partition with its boot files. With Vista or later it is bootmgr & BCD if in BIOS boot mode. And that is what grub looks for not boot flag to find a Windows install to boot.

You need just about any bootable CD or flash drive and move boot flag. Best if you are using Windows to also have a Windows repairCD or flash drive.

If you are booting with grub and getting grub rescue, you should be able to manually boot, but that would indicate that something in Ubuntu is corrupted.

       See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by yancek on 2014-10-07
If I understand correctly, you only had Ubuntu installed and you had an ntfs data partition on that drive, is that correct?
You do NOT have any windows OS installed, correct?
You copied the files from a windows iso file (extracted or just the iso) to this 4GB partition, correct?
Are you trying to boot the windows installation medium on the 4GB drive to install it?  You indicate the installer starts in your last post.
I don't see how changing the boot flag to that partition and copying windows files to it is going to make the changes you are seeing.  Maybe I'm not reading your post correctly?

---

