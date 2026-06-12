---
title: "I put a script in grub.d that broke my bootloader. Drive is encrypted. Can I salvage?"
date: 2020-01-18
forum: General Help
---

### Post by v9yyv7f65x4 on 2020-01-18
As the title says, I did something stupid and put a script in /etc/grub.d that broke my bootloader. All I need to do is get in and delete that file, but I encrypted my drive at installation. Is this recoverable? Or do I need to format?

I can get into the grub command line. And I know Ubuntu was installed on hd1, but not sure which partition.

When I get device info for hd1, this is what I see:

Device hd1: No known filesystem detected - Sector size 512b - Totalsize 488386584KiB
    Partition hd1,gpt1: Filesystem type fat, UUID D976-ED20- Partition start at 1024KiB - Total size 524288KiB
    Partition hd1,gpt2: Filesystem type ext* - Last modification time 2020-01-18 23:24:43 Saturday, UUID 46{....} - Partition start at 525312KiB - Total size 749568KiB
    Partition hd1,gp3: No known filesystem detected - Partition start at 1274880KiB - Total size 487110656KiB

---

### Post by aljames2 on 2020-01-18
These commands can help identify the partition where Ubuntu is installed
```
sudo blkid
```
```
sudo fdisk -l
```

You may be able to use an Ubuntu Live USB drive to restore the bootloader.

---

### Post by oldfred on 2020-01-18
If you can get to grub command line, you should be able to boot by passing broken grub menu.

Change to your partition. Example is (hd0,1) and sda1. You may need to load the grub drivers used for loading encrypted partition, but I do not know those.

grub> set root=(hd0,1)
grub> linux /vmlinuz root=/dev/sda1
grub> initrd /initrd.img
grub> boot

grub rescue:
If you're in the GRUB rescue shell the commands are different, and you have to load the normal.mod andlinux.mod modules:
grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue> set root=(hd0,1)
grub rescue> insmod normal
grub rescue> normal
grub rescue> insmod linux
grub rescue> linux /vmlinuz root=/dev/sda1
grub rescue> initrd /initrd.img
grub rescue> boot

If UEFI you may be able to boot with rEFInd or either UEFI or BIOS with Supergrub.
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[https://www.supergrubdisk.org/rescatux/](https://www.supergrubdisk.org/rescatux/)

I have rEFInd on an old tiny flash drive just for emergency boot. 
And keep a SuperGrub ISO on my multiple boot flash drive with several ISO for repairs.

---

