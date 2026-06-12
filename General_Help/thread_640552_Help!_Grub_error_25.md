---
title: "Help! Grub error 25"
date: 2007-12-14
forum: General Help
---

### Post by joshnackh on 2007-12-14
Hello everyone,

Here is my current setup:
Dell XPS 400 with Vista installed on internal HD
External FireWire HD.

I decided to give Ubuntu a try. So I booted up from the live CD, and selected my external HD as the place to install Ubuntu.

Now, when I boot up, it always hangs while trying to run Grub and gives me Error 25.

I've done some research, and apparently Error 25 means it cannot find the hd or hd failure. I've run HD diagnostics, and concluded that the drive is not experiencing a failure.

So this leads me to believe that my computer is having a hard time booting from a FireWire device. When I enter the boot menu, it only gives me the option to boot from USB, CD, or Primary HD.

When I run Live CD, the FireWire HD shows up, and I can view all the files inside fine.

Here is the output when I sudo fdisk -l, if it helps any:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6daf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6       48163+  de  Dell Utility
/dev/sdb2   *           7       29787   239215882+   7  HPFS/NTFS
/dev/sdb3           29788       30393     4867695   db  CP/M / CTOS / ...

```

FYI, the 120GB drive is the external FireWire, and my internal is the 250GB.

So, as of now, my computer is a giant brick. Any suggestions would be extremely appreciated.

Josh

---

### Post by elliotjreed on 2007-12-14
You could try the following - it helped me and is from Ubuntu user vnbuddy2002...

[I]Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer[/I]

---

### Post by joshnackh on 2007-12-14
I apologize, but you lost me at step 4. I'm fairly new to linux partitioning, and need you to clear up some things. Here is a window of where I'm stuck:
[[IMG]http://img147.imageshack.us/img147/4392/photo121407002wc6.th.jpg[/IMG]](http://img147.imageshack.us/my.php?image=photo121407002wc6.jpg)
So what am I supposed to do now? and what do you mean by

```

/
/boot
swap
.........
```

I want to enjoy ubuntu! Thanks for the advice.

---

### Post by confused57 on 2007-12-14
If your computer won't boot with the external drive disconnected, you can try  a Vista install  DVD(not a recovery disk) and use the bootrec.exe utility to get Vista booting again:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
Would probably be better to disconnect your external drive if you use the Vista DVD.

If you have access to another pc, you could burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You can repair Vista's mbr with the option "Fix Boot of Windows" with SGD.

Then try to boot your external drive, using SGD.

It's probably easier to reinstall grub, using the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Added:  I haven't seen anyone in the forum install Ubuntu to an external firewire hd, so I don't know what problems there might be.
I would suggest you try restoring your Vista's IPL to the mbr, using a Vistal install DVD or SGD, then install grub to Ubuntu's root partition(using the live cd), e.g.
root (hdx,y)
setup (hdx,y)
x,y means just leave these values as "find /boot/grub/stage1" shows.

Once you've done this you might want to use EasyBCD and add an entry to Vista to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

