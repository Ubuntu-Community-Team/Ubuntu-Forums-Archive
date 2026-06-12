---
title: "How to mount the correct partition on installation?"
date: 2022-04-18
forum: General Help
---

### Post by cooperino on 2022-04-18
Ubuntu doesn't install GRUB on the same drive it is being installed into, which is weird that it's not fixed.. because following help in this forum, I managed to do it manually AFTER the installation.

This is the post that helped me: [https://ubuntuforums.org/showthread.php?t=2473897](https://ubuntuforums.org/showthread.php?t=2473897)
So if I managed to do it in fairly simple steps I'm not sure why Ubuntu developers don't think about fixing this issue because it's really annoying

I was wondering if it's possible though to make Ubuntu install itself on the correct drive during installation and not having to mess with all that later.

This is how my fstab looked after the installation:

```
# / was on /dev/sdb5 during installation
UUID=<some_uuid>   /              ext4
# /boot/efi was on /dev/sda2 during installation
UUID=<some_uuid>   /boot/efi    vfat
# /swap was on /dev/sdb4 during installation
UUID=<some_uuid>   /swap    sw
```

as you can see the installation installed GRUB inside /boot/efi of sda instead of /boot/efi of sdb

How should I force it to install on the chosen drive assuming I have multiple physical drives installed?

Thanks!

---

### Post by oldfred on 2022-04-19
Multiple work arounds in old but current bug report.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

While others have suggested disconnecting drives, this probably is easier.
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

---

### Post by cooperino on 2022-04-21
Can confirm that the method of removing flags from the other drives works!

**This time I installed 22.04 so it's either that the method works or they fixed it in this version :P

---

