---
title: "trying to boot into iso of SystemRescueCD, menu entry works but not boot"
date: 2015-04-30
forum: General Help
---

### Post by a-you on 2015-04-30
I'm trying to get grub2 to boot into an iso of SystemRescueCD and I've managed to get it to quasi-work. That is, by creating a folder directly under "/" ("isofile") and putting the iso there and then editing /etc/grub.d/40_custom by adding:

```
menuentry "SystemRescueCd (isoloop)" {
        loopback loop /isofile/systemrescuecd-x86-4.5.2.iso
        linux (loop)/isolinux/rescue64 isoloop=isofile/systemrescuecd-x86-4.5.2.iso
        initrd (loop)/isolinux/initram.igz
}
```

that works, but checking with gparted there's a lock icon next to the / partition and I'm guessing (though I haven't tried it) that if I were to try to recover from the backup to that partition using fsarchiver on the SystemRescueCD distro---which is the whole point of this---that it would be a problem because it would be overwriting the partition the iso is on. I have a separate home partition but when I try to have grub2 boot from an iso there somewhere it doesn't work. The menu entry is shown but it won't boot into that. It seems like I have to somehow specify that it should look in a different partition for the iso. I have tried variations on the above menu entry text that interwebs searches turned up, but none worked.

Anybody know how to do this?? (Thanks in advance!)

ubuntu studio 14.4 64 bit.

---

### Post by oldfred on 2015-04-30
I always have had my ISO on a different drive. Originally on my flash drive, so I could boot several different ISO from one flash drive.
But as soon as I had more than one hard drive then ISO went into their own partition on that drive. You do have to include partition & drive then in loopmount.

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

      
```
 My sda
5      121GB   126GB   5163MB  ext4            iso_ssd
my sdb
 6      993GB   1000GB  7337MB  ext4            iso_hdd


```

---

### Post by a-you on 2015-04-30
Thank you oldfred you are a genius. It's working now. What had been mixing me up was one important detail, which was explained very nicely by drs305 (thanks to drs305 too): "...Since a separate /home partition is only mounted by fstab later in the  boot process, Grub 2 will not find the file if the path is designated  (hdX,Y)/home/*username*/iso/isofilename." That makes sense now that I read it, but that's only now ;-). I read several pages I got to with searches but somehow the combinations of lines in the menu entries were not quite right and it wouldn't boot. And in trying to decide which part to doubt the idea of stripping "home" seemed to make no sense so I kept adding that to the path.

Another interesting point made in one of the pages you linked to was that rescue type distros tend to be designed to run from RAM so that you can for example resize a partition even if you boot from a gparted iso on /, so I guess I didn't need to change things. But I'm glad to have a better understanding of how it works, so thanks a lot.

In case it helps somebody else the menu entry text I have now in /etc/grub.d/40_custom  is:

```
 menuentry "SystemRescueCd" {
        set isofile="/<username>/Documents/downloaded/systemrescuecd-x86-4.5.2.iso"
        loopback loop (hd0,7)$isofile
        linux (loop)/isolinux/rescue64 isoloop=$isofile
        initrd (loop)/isolinux/initram.igz
}
```

which is sort of a hybrid of various attempts. It was basically copied from the SystemRescueCD manual but now with the correct way of specifying the location of the iso.

---

### Post by oldfred on 2015-04-30
Glad to help.

It also took me a while to learn where my ISO were, and with separate drives, I sometime still have issues as my drives change. Boot drive is always hd0 with BIOS. And on my system if I plug in a flash drive it is always sdb which can change my drive order. So both which drive I boot from or which drives are plugged in can can drive order.  
I just had same issue on new system where flash drive became hd0 but I am booting from sda in UEFI mode. Not sure why that is occurring? But I have learned to sometimes just edit grub (hdX,Y) until I find correct X, Y is always same partition on drive.

---

