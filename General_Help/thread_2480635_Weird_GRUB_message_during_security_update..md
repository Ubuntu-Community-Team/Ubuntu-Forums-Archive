---
title: "Weird GRUB message during security update."
date: 2022-11-04
forum: General Help
---

### Post by dalesd on 2022-11-04
I got a Grub update today and it produced a message I don't know how to deal with.  

[IMG]https://i.ibb.co/J2m95pP/image.png[/IMG]

The OS is on sda. (sdb is a storage drive.)   

Do I want to select /dev/sda or /dev/sda4?  
How would I know which is right?

---

### Post by oldfred on 2022-11-04
With Ubuntu's Ubiquity installer, it really does not matter.
It only installs to first  drive's ESP, whatever UEFI/BIOS sees as first drive. Usually sda, but its hd0 in UEFI/BIOS or grub.

You normally always select a drive, but with UEFI it will install to ESP. With BIOS you always select drive like /dev/sda.
If an update, it should have seen correct ESP in fstab. Is fstab have correct entry for ESP?
Post this:

cat /etc/fstab

---

### Post by dalesd on 2022-11-04
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=9bbf45d7-7c4e-48ab-9e15-b906d2182cbc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=54BD-E315  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb3 during installation
UUID=19697fec-b7ea-4540-a00f-b73ba00ad0a7 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=9a1e0856-0250-4ec6-8c87-ff011958aca6 none            swap    sw              0       0

# 4TB data drive (to be removed)
# UUID=3ff73b33-242c-4cec-9494-3dffddaea152 /home/data ext4 defaults,x-gvfs-show 0 2

# A USB drive that got in here somehow, now disabled
# UUID=1AC3-20ED  /boot/efi       vfat    defaults      0       1

# 8TB Toshiba Data drive (to be removed)
/dev/disk/by-uuid/07b337af-af04-4edf-a1f9-267f46ee4a00 /media/Toshiba8TB ext4 nosuid,nodev,nofail,x-gvfs-show 0 0

#  8TB Seagate Data drive
UUID=11d9c072-3c74-4210-9d5b-7b6d7fd24a76   /media/Seagate8T    btrfs   defaults,x-gvfs-show    0   2
#UUID=9bbf45d7-7c4e-48ab-9e15-b906d2182cbc  /boot/efi       ext4    defaults      0       1
UUID=EAD2-2F72  /boot/efi       vfat    defaults      0       1
```

---

### Post by oldfred on 2022-11-04
Part of issue may be that you are showing two ESP in fstab.
Normally you only have one in fstab and if wanting to boot from other directly, you use UEFI menu.
And normally booting of install(s) on other drives should be from default grub install.

---

### Post by dalesd on 2022-11-04
I don't understand.  
This isn't a dual boot system.  

Over the years drives have been added and removed (more than what's shown in the fstab) and it used to be a dual boot system long ago but I thought the last vestiges of that had been [cleared up when a drive failed about six months ago]("https://ubuntuforums.org/showthread.php?t=2475337"). (thanks for your help with that, btw!)

---

### Post by oldfred on 2022-11-04
It looks like you have three entries but two are commented out so should be ok.
Not sure how you got so many entries. Did you reformat the FAT32 & then totally reinstall grub?

```
# /boot/efi was on /dev/sda1 during installation
#UUID=54BD-E315  /boot/efi       vfat    umask=0077      0       1
#  8TB Seagate Data drive
UUID=11d9c072-3c74-4210-9d5b-7b6d7fd24a76   /media/Seagate8T    btrfs   defaults,x-gvfs-show    0   2
#UUID=9bbf45d7-7c4e-48ab-9e15-b906d2182cbc  /boot/efi       ext4    defaults      0       1
UUID=[COLOR=#ff0000]EAD2-2F72[/COLOR]  /boot/efi       vfat    defaults      0       1

```

It looks like your fstab has the 8TB drive's ESP. If external & not plugged in, then that would be why it is asking where to install.
The ESP on sda1 is commented out.
And the other ESP on 8TB drive, is trying to use an ext4 partition is never correct. ESP must be FAT32. I would just remove that entry.

---

### Post by dalesd on 2022-11-04
> **oldfred said:**
> It looks like you have three entries but two are commented out so should be ok.
Not sure how you got so many entries. Did you reformat the FAT32 & then totally reinstall grub?

I don't know. Maybe? Possibly. When that drive died, I tried lots of things to get the system to boot again.  

> 
```
# /boot/efi was on /dev/sda1 during installation
#UUID=54BD-E315  /boot/efi       vfat    umask=0077      0       1
#  8TB Seagate Data drive
UUID=11d9c072-3c74-4210-9d5b-7b6d7fd24a76   /media/Seagate8T    btrfs   defaults,x-gvfs-show    0   2
#UUID=9bbf45d7-7c4e-48ab-9e15-b906d2182cbc  /boot/efi       ext4    defaults      0       1
UUID=[COLOR=#ff0000]EAD2-2F72[/COLOR]  /boot/efi       vfat    defaults      0       1

```

It looks like your fstab has the 8TB drive's ESP. If external & not plugged in, then that would be why it is asking where to install.
The ESP on sda1 is commented out.
And the other ESP on 8TB drive, is trying to use an ext4 partition is never correct. ESP must be FAT32. I would just remove that entry.

Ok, I can edit my fstab later.  

How do I proceed with this?  

[IMG]https://i.ibb.co/J2m95pP/image.png[/IMG]

---

### Post by oldfred on 2022-11-04
Just choose sda.
It probably will update fstab again with a new entry for ESP on sda. 
You then can houseclean out all the old copies.
Just make sure to keep the correct one.
Compare fstab with UUID of mounted ESP.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid

---

### Post by dalesd on 2022-11-04
Ok, thanks.  

I checked /dev/sda and then clicked Next and it asks:  

> Continue without installing GRUB? 
[IMG]https://i.ibb.co/5x9kGn5/image.png[/IMG]
Help message says:  

> You chose not to install GRUB to any devices. If you continue, the boot loader may not be properly configured, and when your computer next starts up it will use whatever was previously in the boot sector. If there is an earlier version of GRUB 2 in the boot sector, it may be unable to load modules or handle the current configuration file.  

 If you are already running a different boot loader and want to carry on doing so, or if this is a special environment where you do not need a boot loader, then you should continue anyway. Otherwise, you should install GRUB somewhere. &#9474;

This doesn't feel right.   
Is this a bug?  
I did tell it to install GRUB on sda. Why is it asking me to continue without installing GRUB?

---

### Post by oldfred on 2022-11-04
You can continue, but then will have to repair grub.
Best then to use Boot-Repair & its advanced options.
Choose total reinstall of grub, choose sda and include latest kernel, so everything boot related is updated.

---

