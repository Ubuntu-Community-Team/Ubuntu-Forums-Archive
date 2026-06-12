---
title: "How to set mount point for new esp partition?"
date: 2022-04-19
forum: General Help
---

### Post by cooperino on 2022-04-19
[COLOR=#232629][FONT=-apple-system]I created a new empty fat32 partition using GParted to install GRUB on, because I want to separate GRUB from Windows Boot Manager.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
but fstab requires a mount point:[/FONT][/COLOR]
```

UUID=ABCD-1234 /boot/efi       vfat    umask=0077      0       1
[COLOR=#232629][FONT=-apple-system]
```

The original mount point in fstab was /boot/efi. What should the mount point be now?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]When I use lsblk the mount point is empty[/FONT][/COLOR]

---

### Post by TheFu on 2022-04-19
Only 1 EFI partition is supported per drive. If you only have 1 drive in the system, then having two is against standards. The single partition is designed to be shared by every OS.  [https://news.ycombinator.com/item?id=16261237](https://news.ycombinator.com/item?id=16261237) has a post by the EasyBCD creator. Worth reading.

To boot a specific drive with EFI, I think you'll manually need to use an efi manager that is built into the BIOS.

---

### Post by yancek on 2022-04-20
You need to clarify what you are doing.  As asked above, are both windows and Ubuntu on the same drive.  If so, the efi files for each OS are separated with the windows files in a directory named Microsoft and the Ubuntu files in a directory named ubuntu.  If you have Ubuntu on a separate drive, you would need to get  the UUID on the second drive of the vfat partition using the blkid command and put that in the Ubuntu fstab file.  The mount point for the new EFI partition would also be /boot/efi with the new UUID.

It isn't clear what you are trying to do.  Do you already have Ubuntu on the same drive with windows are is this going to be a new install of Ubuntu?  If it is a new install, the Ubuntu installer will probably install the Grub files on the first EFI partition which will likely be the same as windows.

---

