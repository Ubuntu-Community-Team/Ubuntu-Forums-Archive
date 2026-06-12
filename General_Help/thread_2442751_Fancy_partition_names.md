---
title: "Fancy partition names"
date: 2020-05-07
forum: General Help
---

### Post by donbcilly on 2020-05-07
I have a little script that allows you to add an ISO to the grub menu, therefore bypassing the need to use live media.
Problem: I can parse names like /dev/sda1 or hda2 etc. and convert the to "grub" notation like hd0,1. But.
Partition names are not returned in that format in all cases by df -P.
Some are like /dev/nvme0p1 (for NVME disks, I suppose).. and others.

Now, I can parse  /dev/nvme ones, but...
How many "types" of partition names am I **likely** to encounter, what are they, and with what "prevalence"?
I mean, things like "/dev/mmcblkXpY" I guess I can safely ignore, but... I'm sure you understand my doubt here.

---

### Post by oldfred on 2020-05-07
Drives used to be hda, but almost all now are sda.
Newer SSDs are NVMe.
Many tablet type devices use MultiMediaCard (MMC).
You then have volumes like RAID or LVM.
Also virtual installs use vda.

I see in grub a line like this, but do not know c code then has extra logic for NVMe & MMC:
/* /dev/[hsv]d[a-z]+[0-9]* */

Bootinfoscript is a command line tool to output info on drives and boot configuration. Used a lot before Boot-Repair, but Boot-Repair actually runs a version of bootinfoscript. Yann has updated his version to include NVMe & MMC devices.

Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)
See post by baedacool of proposed fixed version. Link in pull request
[https://github.com/baedacool/bootinfoscript](https://github.com/baedacool/bootinfoscript)

You can install Boot-Repair and looks at its version 
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
bootinfoscript - yann's version is in
/usr/share/boot-sav/b-i-s.sh

---

### Post by donbcilly on 2020-05-08
Thank you.
I think I can safely assume that **most** drives are either in a /dev/**x**d**y** or in /dev/nvme**x**n**y**p**z** format.
Tablet drives and SD cards don't really apply here - nor should RAIDs.

So something like
[PHP]part=$(df -P . | sed -n '$s/[[:blank:]].*//p')
ptype=${part:5:1}
case $ptype in 
n) p1=${part:9:1};p2=${part:13:1};p4="hd"$p1,$p2                   ;;
s) p1=${part:7:1};p2=${part:8:1};p3=$(tr abcdefghij 0123456789 <<< "$p1");p4="hd"$p3,$p2                         ;; ### $p4 is the grub notation
esac
echo $ptype,$p4
[/PHP]
(no, it's not PHP, it's bash, but with PHP tags it's prettier ;·)

Should work in, like, 99% of cases which is good enough for me :·)

[EDIT] In case you'd like to see the project (it's for KDE), it's here: [https://sourceforge.net/projects/grub-iso-adder/](https://sourceforge.net/projects/grub-iso-adder/)

---

### Post by VMC on 2020-05-08
I have a set grub.cfg that I use. I never use those scripts. I have a way to prevent grub-install to alter my grub.cfg file.
It looks like this for example. All my ISO's are in a separate drive.

```
insmod gfxterm
set gfxmode=640x800
set timeout=30

set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue

menuentry 'Windows' --class windows --class os{
    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root F8B1-15F9
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
menuentry 'ubuntu' --class ubuntu --class gnu-linux --class gnu --class os{
    insmod all_video
    insmod gzio
    insmod ext2
    search --no-floppy --fs-uuid --set=root 5bd4e021-e5fe-47e6-ae95-27d82cbccf95
    linux /boot/vmlinuz root=UUID=5bd4e021-e5fe-47e6-ae95-27d82cbccf95 ro pci=noaer quiet splash
    initrd /boot/initrd.img
}
menuentry 'budgie' --class ubuntu --class gnu-linux --class gnu --class os{
    insmod all_video
    insmod gzio
    insmod ext2
    search --no-floppy --fs-uuid --set=root 5e0ae8e6-1a70-466a-9ae8-906ac1ad071a
    linux /boot/vmlinuz root=UUID=5e0ae8e6-1a70-466a-9ae8-906ac1ad071a ro pci=noaer quiet splash
    initrd /boot/initrd.img
}
menuentry 'xubuntu' --class ubuntu --class gnu-linux --class gnu --class os{
    insmod all_video
    insmod gzio
    insmod ext2
    search --no-floppy --fs-uuid --set=root 0a407ccf-5f8f-46ce-b6a4-1a8ddb4e7821
    linux /boot/vmlinuz root=UUID=0a407ccf-5f8f-46ce-b6a4-1a8ddb4e7821 ro pci=noaer quiet splash
    initrd /boot/initrd.img
}
menuentry 'System setup'{ fwsetup}

submenu ISO {

menuentry "ISO" {
    set isofile="/SAVE/ISO/ubuntu.iso"
    loopback loop (hd2,1)$isofile
    linux (loop)/casper/vmlinuz boot=casper toram maybe-ubiquity iso-scan/filename=$isofile noprompt noswap noeject
    initrd (loop)/casper/initrd
        }
menuentry "lubuntu" {
       set isofile="/SAVE/ISO/lubuntu.iso"
    loopback loop (hd2,1)$isofile
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
       initrd (loop)/casper/initrd
    }
}
```

---

