---
title: "[SOLVED] How to rename RAID-1 arrays ?"
date: 2008-06-05
forum: General Help
---

### Post by dbyrne on 2008-06-05
I have four hard drives in my 7.10 system, 2x300Gb and 2x750Gb.

Six RAID-1 arrays run on these:

```
RAID:       md0   md1   md2
1st 300Gb: sda1  sda5  sda6
2nd 300Gb: sdb1  sdb5  sdb6

RAID:       md3   md4   md5
1st 750Gb: sdc1  sdc5  sdc6
2nd 750Gb: sdd1  sdd5  sdd6

```
md0 is mounted on /, md1 is swap, md2 is mounted on /home.
md3 is mounted on /newroot, md4 is swap, md5 is mounted on /newhome.

I've rsync'd md0 -> md3, md2 -> md5, and would now like to remove the 300Gb pair. I've changed the BIOS so that the 750Gbs are the primary/secondary boot drives instead of the 300Gbs, and changed /newroot/fstab to mount md3 on / and md5 on /home. I've also changed /newroot/boot/grub/menu.lst to load the kernel off /md3.

When I reboot, grub picks up the right menu.lst, but the system drops into busybox with a message to the effect that /dev/md3 does not exist :confused:

Am I right that the 750Gb drives stay as sdc and sdd ? They don't become sda and sdb just because I change the boot sequence ?

Any ideas what's going wrong here ?

edit: the reason for doing this is to eventually rename md3 to md0, md4 to md1 and md5 to md2. I then want to re-format the 300Gb drives and assemble them into md3. Maybe there's an easier way ...

---

### Post by fjgaude on 2008-06-06
Well, in 7.10 they likely will change names when from boot to boot. mdadm doesn't use names but the superblocks of the drives to assemble.

You maybe don't have grab on both set of drive pairs... I have never done what you are doing.

---

### Post by dbyrne on 2008-06-06
You're probably right about not having grub installed - I never know for sure that a disk has grub installed unless it just happens to boot up. It's a matter of blind faith unfortunately ...

FWIW, I did this:

```
$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd2) /dev/sdc
grub> root (hd2,0)
grub> setup (hd2)
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+15 p (hd2,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub> quit
```

Then I did the same for /dev/sdd (the other SATA drive).

edit: OK I've confirmed that /dev/sdc is now repeatably bootable. I changed the /boot/grub/menu.lst on that drive, and verified that this one is being used. The relevant lines are:

```
...
groot=(hd0,0)
...
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=/dev/md3 ro quiet splash
...
```

After five minutes or so, the boot sequence times out, and a message "Device /dev/md3 does not exist" is displayed. 

/etc/mdadm/mdadm.conf reads:

```
DEVICE partitions
...
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=31b1720c:c8844f21:d9f35282:e939850d
```

The disks in the md3 array are:

```

$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 31b1720c:c8844f21:d9f35282:e939850d
  Creation Time : Tue Jun  3 20:57:37 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3

    Update Time : Fri Jun  6 23:23:01 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f7b24dbf - correct
         Events : 0.4


      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1

```

So I'm not sure why /dev/md3 "doesn't exist".

---

### Post by fjgaude on 2008-06-06
I'm really not much help here... you did have it all working correctly with the smaller drives?

What does

```
sudo mdadm -D /dev/md3
```

show, if anything?

One thing you might try is to rename the mdadm.config to something else.

Then simply try to assemble the arrays using mdadm scan:

```
sudo mdadm --assemble --scan
```

and see what that does. A new .config file will be created. Take a look at it.

---

### Post by dbyrne on 2008-06-07
Hi,

Yes, it still works fine with the smaller drives: if I set the BIOS to use them as boot, md0-5 are all assembled fine. The root filesystem on the bigger drives is a clone of the smaller drives, but booting off those gives the mysterious "/dev/md3 not found".

I'm no expert, but this is my somewhat simplistic view of what I think happens when the system boots up off the small drives:
1. boot loader code runs from the MBR on the boot disk identified by the BIOS, and gets the location of the kernel, initrd etc.;
2. boot loader runs the kernel, which scans for UUIDs of RAID partitions, and assembles these into arrays where the UUIDs match;
3. RAID arrays are mapped by UUID to the RAID devices in /etc/mdadm/mdadm.conf;
4. filesystems in /etc/fstab are mounted on the RAID devices.

I'm sure I've got this wrong as I don't understand how the boot loader can run a kernel on a device that hasn't been assembled yet, or how it can map arrays to devices if the devices haven't been brought up - chicken and egg ?

Anyway, my hypothesis is that maybe only md0 is assembled during the boot sequence, so the system can't find the kernel specified in menu.lst. Either that or it can't find /dev/md3 when it come to mounting the root filesystem on it. Wonder if it would work if I specified UUIDs in the menu.lst line and fstab ? Probably not ...

---

### Post by fjgaude on 2008-06-08
I think you likely have it more correct than in error... from my experience mdadm uses the superblocks to assemble an array, not the UUIDs.

For raid1 to work there has to be a full grub, boot, menu.lst on the boot disk. For it to work when one disk fails you have to have an image of it all on both drives. So you have to make sure the MRB points to each drive that it is to boot from.

So, in your placement of grub on the MRB did you do this on both drives? And then make sure the BIOS points to the one that it's boot from.

There is HOW-TOs in google on doing this... I've never been inclined to want to how just how.

---

### Post by dbyrne on 2008-06-08
The output from "mdadm -D /dev/md3" is:

```
# mdadm -D /dev/md3
/dev/md3:
        Version : 00.90.03
  Creation Time : Tue Jun  3 20:57:37 2008
     Raid Level : raid1
     Array Size : 9767424 (9.31 GiB 10.00 GB)
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Sun Jun  8 17:35:51 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 31b1720c:c8844f21:d9f35282:e939850d
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
```

so all looks good. So here's what I've tried today:

1. Change root=/dev/md0 in /boot/grub/menu.lst to UUID=*<uuid of /dev/md0 as given by "vol_id -u /dev/md0">*

2. Change all /dev/md* to equivalent UUIDs in /etc/fstab

Reboot to make sure this works - everything came up OK.
Then I did the same on the new bigger disks, which previously had  failed to boot, with the "Device /dev/md3 does not exist" message. Predictably, this time the boot hung up and dropped to Busybox with "Device UUID=*<uuid of /dev/md3>* does not exist".

Well at least it's behaving predictably. The only other difference I can find between the disks that make up md0 (which boots) and md3 (which doesn't), is that the latter (/dev/sdc1 and /dev/sdd1) are marked Bootable. This is probably irrelevant, as they are the ones that *don't* boot, but I've fdisked them off and will try to boot off them later now that everything looks identical.

---

### Post by fjgaude on 2008-06-08
Hang in there and soon you will achieve success!

Wish I could help more... but I'm as lost as you.

---

### Post by dbyrne on 2008-06-08
Well I got it sorted - you're right, sometimes it just takes enough fiddling around to hit on the solution :)

Just after I had removed the bootable flags off the new drives, I also noticed that the initrd on the new pair was smaller than the one on the old drives, so on the offchance that the raid1 module wasn't loaded, I did an update-initramfs, making sure the raid1 module was included (I whish I'd checked to see that it wasn't already loaded first). Anyway that gave me a new initrd, the same size as the one on the old drives. I've no idea why they were different anyway, as the rsync I did should have made them identical ...

Some one of these steps made the difference, as the system then booted up on the new drives. So the problem is solved, but I'm not exactly sure which correction was responsible - was it the move to UUIDs that corrected some typo, or the update-initramfs, or the bootable flags ? I guess I'll never know. Oh well !

---

### Post by fjgaude on 2008-06-08
Hoorah! Success... happy for you.

---

### Post by dbyrne on 2008-06-08
Thanks for your encouragement Frank, I was tearing my hair out at times :)

---

