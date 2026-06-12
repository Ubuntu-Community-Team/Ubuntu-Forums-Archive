---
title: "Getting I/O errors but multiple hurdles in way of resolution"
date: 2023-07-04
forum: General Help
---

### Post by adam-hardy on 2023-07-04
I'm running Ubuntu 22.04.2 and XFCE. I'm currently ripping a bunch of DVDs and I guess I've hit a bad area of the file system because it foobars ubuntu. Suddenly every command I try to execute won't run and all the bits of the window manager crash, I see I/O errors come up, not even the tty login works and I end up hard booting. 

I want to boot to repair mode but I have a couple of issues there. First of all, the graphics are up the creek - the interface is too big for the screen - so I can't operate in repair mode nicely. Is there a simple solution to that? 

Secondly when I do manage to get to do something, I get an error message about a drive I mounted 10 years ago but have now no recollection of - sorry but my memory is crap, I must sleep more. Here's the error message - how do I get rid of the mapping of the remote host edoras? I obviously never  use that and should have removed it after I finished playing around with it years ago.

```

fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/mapper/edoras--vg-root  is mounted
e2fsck:  Cannot continue, aborting
```

---

### Post by TheFu on 2023-07-04
Running fsck is not allowed to mounted file systems.  The easiest solution is to boot into rescue mode - this is under the grub "Advanced" menu.  In rescue mode, you can run **fsck** against all file systems. It should be a menu option.

If that doesn't correct all reported issues, then I'd suspect the storage device is failing. Get your precious data off it ASAP, then you can run **smartctl** to look at the SMART data for the SSD/HDD and decide if it is failing or not.  **smartmontools** is the package.

*/dev/mapper/edoras--vg-root* tells me that you checked the "Use LVM" check box during install. This means you are using the LVM volume manager which makes things a little more complex but provides many, many, enterprise options.  For example, if you need a new HDD, moving everything under LVM control to a new storage device is pretty simple.  
/dev/mapper/edoras--vg-root tells me that the VG name is "edoras-vg" and that "root" is the LV name. Those two items are important for many LVM commands.  To see a summary of everythign LVM on your system, run these 3 commands:
```
sudo pvs
sudo vgs
sudo lvs
```
You can also use
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint

``` for an overview.

If you need to replace the old LVM storage, connect the new storage, create a new partition to hold the old LVM stuff (make it at least the size of the old LVM PV, then use **pvmove.** That will move all PVs, VGs and LVs on that specific source device to the new storage. The system can be running and used while all this happens.  This won't move non-LVM partitions and file systems. For those, you'll want to use some other tool, perhaps **gparted**?

---

### Post by ActionParsnip on 2023-07-04
You can't fsck a mounted file system. You'll need to boot to an Ubuntu Live USB/CD (or similar) and fsck it there. Alternatively you can run:
```

touch /forcefsck

```
Then reboot and it should check at next reboot

---

### Post by TheFu on 2023-07-04
> **ActionParsnip said:**
> You can't fsck a mounted file system. You'll need to boot to an Ubuntu Live USB/CD (or similar) and fsck it there. Alternatively you can run:
```

touch /forcefsck

```
Then reboot and it should check at next reboot

```
touch /forcefsck
```
hasn't worked since systemd took over. Yet another thing that was working well, convenient, that systemd broke.

---

### Post by ActionParsnip on 2023-07-04
> **TheFu said:**
> ```
touch /forcefsck
```
hasn't worked since systemd took over. Yet another thing that was working well, convenient, that systemd broke.

Then live USB / CD it is

---

### Post by TheFu on 2023-07-04
> **ActionParsnip said:**
> Then live USB / CD it is

Or use the _Rescue Mode_ from the Grub menu "*Advanced*".  There is a grub boot command that can be entered to force an fsck too, but I always have to look it up.

---

### Post by adam-hardy on 2023-07-04
Thanks for all the messages but the first problem is booting into rescue mode brings up a console dialog which is far too big for the screen so i can't read half of it and any messages scroll off out of sight.

edoras is a host at my hosting provider which a few websites on that I have. The machine I'm talking about with this I/O problem is my server sitting in my living room. i don't remember how i connected them up but i do see some stuff in fstab:

```
[FONT=system]
[FONT=courier new][SIZE=3]/dev/mapper/edoras--vg-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=1A06-1FED  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/edoras--vg-swap_1 none            swap    sw              0       0
LABEL=Seagate-4TB /media/backuppc/usbbackup auto defaults 0 1
/mnt/3GiB.swap swap swap defaults 0 0[/SIZE][/FONT]
[/FONT]
```

The output of `lsblk`confuses me completely. 

```

[FONT=courier new]adam@gondolin:~$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                  TYPE FSTYPE        SIZE FSAVAIL FSUSE% LABEL                      MOUNTPOINT
sda                   disk               3.6T                                           
&#9492;&#9472;sda1                part ext4          3.6T      2T    38% Seagate-4TB                /media/backuppc/usbbackup
sdb                   disk               1.8T                                           
&#9492;&#9472;sdb1                part ext4          1.8T  875.3G    47% Videos-2TB                 /media/adam/Videos-2TB
sr0                   rom  udf           7.9G       0   100% HAENDE_WEG_VON_MISSISSIPPI /media/adam/HAENDE_WEG_VON_MISSISSIPPI
nvme0n1               disk             476.9G                                           
&#9500;&#9472;nvme0n1p1           part vfat          512M  504.9M     1%                            /boot/efi
&#9492;&#9472;nvme0n1p2           part LVM2_member 476.4G                                           
  &#9500;&#9472;edoras--vg-root   lvm  ext4        475.5G  188.2G    55%                            /
  &#9492;&#9472;edoras--vg-swap_1 lvm  swap          980M                                           [SWAP]
[/FONT]
```

So, what on earth is 'edoras' doing in there? I wish I could go back in time and give myself a slap. Please correct me if I am wrong but my nvme0n1 is partitioned into a boot partition and another partition, which is subpartitioned into partitions which are named after another host??? I must have been smoking crack at the time.

---

### Post by TheFu on 2023-07-04
```
nvme0n1               disk             476.9G                                           
&#9500;&#9472;nvme0n1p1           part vfat          512M  504.9M     1%                            /boot/efi
&#9492;&#9472;nvme0n1p2           part LVM2_member 476.4G                                           
  &#9500;&#9472;edoras--vg-root   lvm  ext4        475.5G  188.2G    55%                            /
  &#9492;&#9472;edoras--vg-swap_1 lvm  swap          980M                                           [SWAP]
```

This is a standard "Use LVM" checkbox install.  The installer decided to name the VG group something it thought would be unique, "edoras-vg".
Those aren't partitions. They are LVs, because you are using LVM.

/boot/efi is required to be FAT32 by the EFI standards. No choice on that.
/ really shouldn't be larger than 35GB in size and you should have reduced that size to 35GB immediately post install for many reasons.  The command back then was **lvreduce**.  You've put too much junk on it at this point.
The swap LV is just under 1GB.  That's usually too small for any desktop, but could be fine for a server.  IME, swap on a desktop, regardless of RAM, should be 4.1GB.  This provides enough room for huge bloated programs to be swapped out (modern browsers) and for end users to "feel" the system getting slow before it crashes.

When using LVM, there are a few key ideas.  
a) only setup LV sizes to be what you need for the next 3 months.  Adding more as needed is 5 seconds, provided you have free space in the VG.  If you allocate all the VG to LVs, there's little you can do later when the real location for different data is known.  If everything is in a single mount point (like you have with the "root" LV above), then you cannot mount different parts with different mount options to improve system security.  Also, if all the VG is already allocated, then you can't create snapshots for all the great reasons we love snapshots.  Basically, if you aren't going to use LVM's features, why bother?

As for names of stuff being the same on 2 different systems.  I certainly didn't set that up.  You must have.  You'll need to keep them separate in your mind.  Hardware issues on your web host aren't your problem.  Complain to them, if you see any I/O issues on a rented system.  

If this is in your house, then it is your problem. If you can't see the rescue menu, then try booting from an Ubuntu Desktop ISO. Remember the flash drive you created to do the install?  Use that.  then you'll run fsck manually.  Point at the LV devices after you use LVM tools to have all the disks scanned. Don't mount them, just get the list from the **sudo vgs** and **sudo lvs** commands I've already posted.

If fsck doesn't make the issues go away, then it is time to hunt down the real hardware issue and prepare to replace that hardware.

---

