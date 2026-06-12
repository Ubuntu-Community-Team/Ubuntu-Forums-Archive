---
title: "reinstall grub after installing windows over a legacy grub"
date: 2016-02-04
forum: General Help
---

### Post by lagarkane on 2016-02-04
Hi!

I know this question seems relatively standard, and I already see you pointing me to the miriad of threads we can find on internet about this issue.
But there is an additional problem:

I wanted to follow the standard procedure to reinstall my grub after installing Windows. I booted on a 14.04 live usb, and typed "grub-install /dev/sdX" to fix my grub. But on Ubuntu, grub is not the old legacy version, but grub2.
I tried booting on a 12.04 live usb key, but for some reason, I cannot pass the menu (I click on "try Ubuntu without installing", get a gray screen, and then my laptop reboots without the USB...)

So the question now is, how can I fix my old legacy grub (and upgrade to grub to by the same time would be great) without reinstalling my system? :/

Thanks in advance!

---

### Post by leunam12 on 2016-02-04
you have to chroot:
```
mount /dev/sdx /mnt
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc
chroot /mnt
```

Then
```
update-grub
grub-install /dev/sdx
```

Then unmount
```
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/sys
umount /mnt/proc
umount /mnt
``` Then reboot

---

### Post by oldfred on 2016-02-04
While chroot is a good way, if you have grub legacy, you need to do a full uninstall and then a reinstall of grub2 as part of chroot. Grub2's package name is grub-pc for BIOS/MBR.

       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[URL="http://ubuntuforums.org/showthread.php?t=1470597"]http://ubuntuforums.org/showthread.php?t=1470597

[/URL]
 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

It might be easier to use Boot-Repair's advanced mode to fully uninstall & reinstall grub. 
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    


[URL="http://ubuntuforums.org/showthread.php?t=1470597"]
[/URL]

---

