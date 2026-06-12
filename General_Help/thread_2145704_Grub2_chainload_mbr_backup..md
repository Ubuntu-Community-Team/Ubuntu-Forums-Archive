---
title: "Grub2 chainload mbr backup."
date: 2013-05-16
forum: General Help
---

### Post by nathema on 2013-05-16
**Situation**:
My company laptop with Windows is secured with McAfee Endpoint Encryption, formerly known as SafeBoot.
SafeBoot uses a custom MBR.
SDA1-SDA3 are Windows partitions. SDA4 is available.
I managed to install Ubuntu besides Windows with the following steps:
[LIST=1]
[*]backup MBR with from Ubuntu Live
```
dd if=/dev/sda of=/path/mbr-backup bs=512 count=1
```
[*]shrink windows volume
[*]install ubuntu-gnome on new partition /dev/sda4 with grub setup on usb stick.
[/LIST]

**Problem**:
[LIST=1]
[*]I do not wish to boot from USB / CD for Linux
[*]Altering the windows bootloader with EasyBCD is out of scope, as it costs money in a company environment.
[/LIST]

**Wish**:
DualBoot Windows/Linux and boot Windows by chainloading the SafeBoot MBR image from Grub2.

**Question**:
Can I chainload a MBR image in Grub2?

Extra info:
@ [http://ubuntuforums.org/archive/index.php/t-1429326.html](http://ubuntuforums.org/archive/index.php/t-1429326.html) Someone tries to chainload a MBR image but fails. His question is unanswered.
@ [http://ubuntuforums.org/showthread.php?t=1039401](http://ubuntuforums.org/showthread.php?t=1039401) My inspiration.

---

### Post by dino99 on 2013-05-16
usually the mbr is used to install grub2 (aka sdx), but the lbr can also be used (aka sdxx, like sda4)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

more info with the link below

---

### Post by nathema on 2013-05-16
> **dino99 said:**
> usually the mbr is used to install grub2 (aka sdx), but the lbr can also be used (aka sdxx, like sda4)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

more info with the link below

Installation of Grub is no issue, my question is about it's configuration so that a menuentry chainloads an image (backup of a MBR).

---

### Post by nathema on 2013-05-16
Last post at [http://forums.gentoo.org/viewtopic-t-660773-start-0.html](http://forums.gentoo.org/viewtopic-t-660773-start-0.html) suggests it's possible. I'll try this!

---

### Post by nathema on 2013-05-17
I succeeded booting the MBR image with the following lines in /etc/grub.d/40_custom:
```

menuentry "Windows 7" {
   insmod lvm
   chainloader (lvm/ubuntu-root)/safeboot.mbr
   boot
}

```

**Problem**:
Booting windows corrupts the linux partition and results in kernel panics or bad superblocks.

**Theory**:
Safeboot.mbr contains the first 512 bytes of the old boot record. This contains the old partition table.
Maybe loading this overwrites the partition table in the new Grub2 MBR.

**Question**:
Is it maybe possible to load safeboot.mbr with only the first 446 bytes which contain the code, but not the partition table and boot signature?

If not, is it possible to overwrite 447-512 bytes with the new partition table?

---

### Post by oldfred on 2013-05-17
While you may be able to modify partition tables, grub2 also writes core.img into about 37 sectors following the MBR, or in the space after MBR & before first partition. There used to be conflicts with DRM software but grub2 now writes around sector 32 where flexnet usually wrote its data.
But I would expect any decent safe boot system would not let you modify all that data without complaining or correcting it.

Would it just not be easier to put a full install of Ubuntu on an external hard drive or newer larger flash drive. I have full installs on several flash drives and while a bit slower once booted work reasonably well if you change a few settings to reduce writes.

---

### Post by nathema on 2013-05-27
> **oldfred said:**
> While you may be able to modify partition tables, grub2 also writes core.img into about 37 sectors following the MBR, or in the space after MBR & before first partition. There used to be conflicts with DRM software but grub2 now writes around sector 32 where flexnet usually wrote its data.
But I would expect any decent safe boot system would not let you modify all that data without complaining or correcting it.

Would it just not be easier to put a full install of Ubuntu on an external hard drive or newer larger flash drive. I have full installs on several flash drives and while a bit slower once booted work reasonably well if you change a few settings to reduce writes.
Indeed.

Everytime I boot into the encrypted Windows, Windows itself or McAfee Endpoint Encryption copies the partition table from the MBR image to the real MBR. This I could fix. But it also destroys the grub data in the sectors passed the MBR. 

I abandon this project.

I will go full Ubuntu with my corporate Windows in VirtualBox.

---

### Post by gacb on 2013-08-08
It's probably easier to install grub-customizer from the PPA. It doesn't reorder the grub menu, but it does allow for choosing the default boot.

---

