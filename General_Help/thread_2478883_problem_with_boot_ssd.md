---
title: "problem with boot ssd"
date: 2022-09-07
forum: General Help
---

### Post by jgw on 2022-09-07
I have a 1tb boot ssd.  Its suddenly started to give me problems.  The first one was on boot when it told me that I had to run fsck manually to fix something.  The problem is that it never told me the options to use.  I now have that ssd on another machine and thought to test it but couldn't find anything that would check the ssd or the grub partition.  

Any thoughts on this one would be helpful.

---

### Post by sudodus on 2022-09-07
1. Check the S.M.A.R.T. status.

This link shows a quick way to do it with Disks alias **[FONT=Courier New]gnome-disks[/FONT]**.

A more advanced tool is **[FONT=Courier New]smartctl[/FONT]**. Install it with the package **[FONT=Courier New]smartmontools[/FONT]**. You find instructions in the manual [FONT=Courier New]**man smartctl**[/FONT].

2. Check [and try to fix] the file system.

If ext2, ext3 or ext4 file system, you can use the following command line,
```

sudo e2fsck -f /dev/sdxn

```
where x is the device letter and n is the partition number.

If a Microsoft file system, FAT32, exFAT, NTFS, use Microsoft tools: run Windows and use **[FONT=Courier New]chkdsk /f X:[/FONT]** where X: is the partition 'volume label' as seen by Windows or use the tool with a graphical user interface.

3. See also [this link](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors/972983#972983)

---

### Post by jgw on 2022-09-07
Thank you for the response!

I tried with disks and it wouldn't let me mount the bios boot partition.  The smart data and self-tests were greyed out.  

I will try and install smartctl and give that one a shot.  I don't have a microsoft machine.  

Got it installed:
$ sudo smartctl -i /dev/sdd1 (this is the first/boot partition)

I tried a short test but nothing seemed to happen.  then I ran this:
```

smartctl -a /dev/sdd1
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-47-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Vendor:               TO Exter
Product:              nal USB 3.0
Revision:             0104
Compliance:           SPC-4
User Capacity:        1,024,209,543,168 bytes [1.02 TB]
Logical block size:   512 bytes
Physical block size:  4096 bytes
LU is fully provisioned
Logical Unit id:      0x3020150331000810
Serial number:        2015033100081
Device type:          disk
Local Time is:        Wed Sep  7 11:52:45 2022 PDT
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Disabled or Not Supported

=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK
Current Drive Temperature:     0 C
Drive Trip Temperature:        0 C

Error Counter logging not supported

SMART Self-test log
Num  Test              Status                 segment  LifeTime  LBA_first_err [SK ASC ASQ]
     Description                              number   (hours)
# 1  Background short  Completed                   -       0                 - [-   -    -]

```

Now I have to try some tests.  I can try the short one again:
root@greg-hp-8200:/home/greg# smartctl -t short /dev/sdd1
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-47-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Short Background Self Test has begun
Use smartctl -X to abort test



```

smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-47-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Vendor:               TO Exter
Product:              nal USB 3.0
Revision:             0104
Compliance:           SPC-4
User Capacity:        1,024,209,543,168 bytes [1.02 TB]
Logical block size:   512 bytes
Physical block size:  4096 bytes
LU is fully provisioned
Logical Unit id:      0x3020150331000810
Serial number:        2015033100081
Device type:          disk
Local Time is:        Wed Sep  7 11:26:23 2022 PDT
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Disabled or Not Supported

```

I ran the short test again and, this time, gave it about 15 minutes.  I got nothing but, perhaps, it doesn't say when its done.

I have no idea what I should do next.  

Thoughts?```

```

---

### Post by sudodus on 2022-09-08
The bios boot partition in a GUID partition table (GPT) is very small and has no (should have no) file system. It contains part of the grub bootloader that used to be before the first partition in a MSDOS partition table. If grub works, there is no need to check it. Otherwise, reinstall grub.

You should run smartctl on the whole drive, not on partitions, so /dev/sda (not /dev/sda1, /dev/sda2 etc).

---

### Post by jgw on 2022-09-09
Thank you for the replies.

I put faith in the ubuntu installer.  It said that it was going to re-do all the partitions on the ssd.  I am assuming that it would do that so it wouldn't matter what was on the ssd.  I have done that several times and never had a problem.  I can goto gparted and just re-partition to one big one and then try to install again.  I guess I could also put on a file system but, I suspect, the installer would do that after it did its own partition thing.  I suspect that should take care of any problems.

---

### Post by yancek on 2022-09-10
> I tried with disks and it wouldn't let me mount the bios boot partition  

You need to clarify that comment.  As pointed out above, if sdd1 shows as bios_boot partition in GParted it should also show as unformatted, no filesystem.  This partition has a specific purpose explained in the earlier post and is used only on a GPT disk to boot in Legacy mode.  That means you can't run fsck on it because there is no filesystem to check and also can't be mounted.

Do an online search for 'how to run fsck' and you should get numerous hits of sites with explanations of the various options.  

>   I can goto gparted and just re-partition to one big one and then try to install again  

I would not do that but rather, post the output of the command:

```
  sudo parted -l
```

That will tell the type of drive (gpt) and show whether you have a gpt drive.  If you have a Legacy install on the gpt drive, you need the bios_grub unformatted partition. You might also post the exact error you get.

---

### Post by jgw on 2022-09-13
Thanks ffor the help!

I did a new installation of 22.04 (erase the whole ssd)  That worked.  Took me all day to install radarr, sonarr, kodi, and a bunch of other stuff but everything is working well so far.

---

