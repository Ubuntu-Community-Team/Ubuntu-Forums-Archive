---
title: "Two mounting questions"
date: 2006-08-26
forum: General Help
---

### Post by Metroid48 on 2006-08-26
Hi, two things. First, which is sort of a minor problem. I have a FAT32 20 GB partition mounted to sdb1 but on the desktop and nautilis it shows up as _PNG and has some weird square underneath it. See attached picture. However, it can still be browsed fine.

Okay, second question. I have a friend who has an Pentium 3 in his computer. He has two internal harddrives, made by Western Digital, one 160 GB and the other 5Gb. Ubuntu seems unable to mount them. They appear in the devices list and in System->Admin->Disks, but they won't mount. It keeps saying he doesn't have permission. He only tried this on the Ubuntu live CD. BTW, he can mount external USB drives fine.

Anyway, thanks in advance,
-Metroid48

---

### Post by meng on 2006-08-26
Your friend needs to specify a mountpoint for the internal HDDs, by modifying /etc/fstab. External drives, floppies, CD-ROMs and flash USBs have predetermined mountpoints within /media.

---

### Post by Metroid48 on 2006-08-26
Yes, but doesn't fstab require a restart for re-mounting, which won't work in the live cd? Also, doesn't Ubuntu live cd automatically generate an fstab file with all the drives named?

Also, any ideas about the weird filebrowser name for /media/sdb1?


EDIT: note that the owner of sdb1 seems to be root, group: plugdev. It won't let me change this, for some reason.

---

### Post by DeShark on 2006-08-26
Sounds silly, but is he using "sudo mount" to mount? Also, where is he trying to mount the drives?

P.s. Fstab doesn't necessarily require a reboot, you can run "mount -a" to mount every device in fstab. Then again, he may as well use the "mount" command to mount the drives. Are they both IDE drives (hda, hdb) or are they SCSI or RAID, etc?

---

### Post by Metroid48 on 2006-08-26
This is all that's in his fstab:

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

He's using a live cd. BTW, typing:

```
sudo mount /dev/hda1 /media/sdb1
```

Got it mounted, but only the root user can read it and it won't allow him to change the permissions or groups or owners. Also, it says that it cannot allow reading for groups because the disk is read-only. Any ideas.


Also, any ideas about the _PNG-weird_symbol problem?

---

### Post by Metroid48 on 2006-08-26
Hi, what can I do to fix the weird _PNG problem (see first post)? It also won't let me unmount it.

---

### Post by aysiu on 2006-08-26
Do this: ```
sudo umount /media/sdb1
sudo mkdir /recovery
sudo mount -t vfat /dev/hda1 /recovery -o iocharset=utf8,umask=000
sudo ln -s /recovery ~/Desktop/recovery
```

---

### Post by peabody on 2006-08-27
Are these drives fat32 or ntfs?

---

### Post by Metroid48 on 2006-08-27
Thanks aysiu, that gets it working closer to what it's supposed to do.

Anyway, my friend's going to install Ubuntu now, so fstab can probably be modified.

Thanks, just one las thing. How can I change the weird _PNG thing? (see first post)

Thanks,
-Metroid48

---

### Post by Metroid48 on 2006-08-27
Ack, my friend can't get it to boot. His BIOS doesn't support USB boots, and he's not going to install GRUB on his main disk

Anyway, any suggestions on how to fix this _PNG drive name thing? Or the weird plugdev group and root user that I can't change?

-Metroid48

---

