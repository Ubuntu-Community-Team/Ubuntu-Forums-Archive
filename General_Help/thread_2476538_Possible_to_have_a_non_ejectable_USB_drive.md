---
title: "Possible to have a non ejectable USB drive?"
date: 2022-06-29
forum: General Help
---

### Post by dinkidonk on 2022-06-29
I have a USB drive which is always attached to the computer and I would like that particular drive not to be listed as ejectable in "system tray" and file manager(s). Is that possible?

---

### Post by sudodus on 2022-06-29
You can try this way:

- create a mountpoint at [FONT=Courier New]**/mnt**[/FONT], for example[FONT=Courier New]** /mnt/myusbdata**[/FONT]

```

sudo mkdir /mnt/myusbdata

```

- add lines in [FONT=Courier New]**/etc/fstab**[/FONT] where you mount the drive at that mountpoint. Then after next reboot, it should get mounted automatically there.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=81deaec8-85dd-49d7-adf5-32bc4c3bbfc2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb3 during installation
UUID=7223-0B34  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda2 during installation
UUID=4b882c9f-4867-4c5c-8eb7-c84ef03f4786 none            swap    sw              0       0
[COLOR="#0000CD"][B]# test for usb drive
UUID=696C-99AC                            /mnt/myusbdata vfat     rw,user,uid=1000,dmask=007,fmask=117 0 0
[/B][/COLOR]

```

I tested it and it works. Please notice the boot options (field #4): they match FAT32 (and I think they would work for NTFS and exFAT too). If you have ext4 or some other linux file system you need other boot options.

Please notice that, if the USB drive is absent, there will be problems at boot, because the system expects there to be drives with partitions with UUIDs for each of the lines in /etc/fstab (except the comment lines).

---

### Post by dinkidonk on 2022-06-29
Thank you for your idea, but that would not work since the drive is encrypted.. I have also looked at the "/sys/block/sd*/removable" attribute but that is already "0".

---

