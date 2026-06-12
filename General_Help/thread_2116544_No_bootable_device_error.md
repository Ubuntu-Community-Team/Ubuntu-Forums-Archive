---
title: "No bootable device error"
date: 2013-02-16
forum: General Help
---

### Post by WhipLash365 on 2013-02-16
Hello,
Yesterday when i turned on my PC i got a black screen with error: "No bootable device - insert boot disk and press any key". It may have something to the disk partition i have deleted because the filesystem was broken (more specifically it was sda1, OS is installed on sda6). I have tried almost everything: manual GRUB2 install using terminal,  Automatic repair via boot-repair, I have deleted GRUB2 and installed it again, repaired MBR and nothing happens. Checked on Google and nothing helped.  But if i insert boot cd and select Boot From Hard Drive everything works fine. What can be the problem then? My OS is Ubuntu 12.10 64-bit.
Output of fdisk -l:
/dev/sda1                63   647016447   323508192+  83  Linux
/dev/sda4         647018494   781422591    67202049    5 Extended
/dev/sda5         773171200   781422591     4125696   82  Linux swap / Solaris
/dev/sda6   *   647018496   773171199    63076352   83  Linux

I dont know why sda1 appears as linux, it is a NTFS partition.
If anyone can help, I sure would appreciate it

---

### Post by dino99 on 2013-02-16
from the livecd/liveusb, run:

sudo grub-install /dev/sda
sudo update-grub

---

### Post by carl4926 on 2013-02-16
Can you get us a screen from Gparted?

---

### Post by WhipLash365 on 2013-02-16
> **dino99 said:**
> from the livecd/liveusb, run:

sudo grub-install /dev/sda
sudo update-grub

Well, I have already tried it. Also if i press Shift during system booting (using LiveCd -> Boot From HDD) GRUB menu will appear, so its not GRUB's fault.
---------------------------------------------------
Here's screen from GParted:
[IMG]http://img405.imageshack.us/img405/6114/screenshotfrom201302161.png[/IMG]

---

### Post by carl4926 on 2013-02-16
Boot the Live CD that you originally used when you installed Ubuntu

Open a teminal

And do:
* Mount your root

```
sudo mount /dev/sda6 /mnt
```

    
* Now mount the rest of your devices

```
sudo mount --bind /dev /mnt/dev
```

    * Now chroot into your system

```
sudo chroot /mnt
```

    *

      When that is done you need to run update-grub to create the configuration file.

```
update-grub
```

    *

      install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

```
grub-install /dev/sda
```

And your done

---

### Post by oldfred on 2013-02-16
A few BIOS check partition table and have to find a primary partition with the boot flag.
Grub does not use boot flag, but Windows has to have a boot flag on the NTFS partition you use to boot from, make repairs, or install into. 
Your boot flag is on the Linux logical partition. I might also move it back to sda1.

Also does sda1 still show as Linux in fdisk? gparted says it is NTFS.

If fdisk still says Linux, I might see what Disk Utility says and see if you can change to 07 NTFS. Do not reformat, just change type. You can also change boot flag with Disk Utility.

---

### Post by WhipLash365 on 2013-02-16
Moving the boot flag worked!
Thanks for help :) 
Also changing to NTFS succeeded and now fdisk shows:
     Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   647016447   323508192+   7  HPFS/NTFS/exFAT
/dev/sda4       647018494   781422591    67202049    5  Extended
/dev/sda5       773171200   781422591     4125696   82  Linux swap / Solaris
/dev/sda6       647018496   773171199    63076352   83  Linux

---

