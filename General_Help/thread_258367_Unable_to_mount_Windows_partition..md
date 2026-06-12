---
title: "Unable to mount Windows partition."
date: 2006-09-15
forum: General Help
---

### Post by sprinkles on 2006-09-15
I can't seem to mount my NTFS windows partition.

```
richard@Llama:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
dmesg | tail brings up
```
[4295605.800000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4295605.800000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4295605.800000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
```

Any ideas?

---

### Post by canadianwriterman on 2006-09-15
My fstab entry for Windows is a little different. I don't know if it makes a difference, but I created a **windows_ntfs** directory, then edited fstab to include:

```
/dev/hda1  /media/windows_ntfs  ntfs  nls=utf8,umask=0222  0  0
```

Then I saved and rebooted. It worked for me.

---

### Post by Popno on 2006-10-11
I got the same messages (exactly!) from Ubuntu about my hard drive mounting.  My problem turned out to be that the 'fdisk -l' told me my partition was NTFS, but it was really FAT32.  So I had to add the line:

   /dev/hda5 /windows vfat iocharset=utf8,umask=000 0 0

instead of the NTFS line into the fstab file.  It worked for me the first time.  I was so excited!

Anyway, I hope that helps.

---

### Post by aysiu on 2006-10-11
I don't know if it makes a difference, but you appear to have an extra slash after /media/windows ```
richard@Llama:~$ sudo mount /dev/hda1 /media/windows**/** -t ntfs -o nls=utf8,umask=0222
```

---

