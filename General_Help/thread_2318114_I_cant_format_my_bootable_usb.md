---
title: "I cant format my bootable usb"
date: 2016-03-23
forum: General Help
---

### Post by v6rg2 on 2016-03-23
I make a bootable usb flash memory for ubuntu 15.10 by **mkusb**. And now want to delet those files and use it for regular uses. But I cant delete anything and cant format in neither Linux or Windows.
It is read only. What could I do?

---

### Post by sudodus on 2016-03-23
You can use mkusb to wipe it and create a new partition table and file system. See this link

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by v6rg2 on 2016-03-23
I wiped my usb by mkusb. Now my Ubuntu dont recognize it. So I must create a partition on it. ok?
In mkusb, what type of partition table should I choice?

---

### Post by sudodus on 2016-03-23
The standard partition table for pendrives is **MSDOS**, and the standard is to have one partition with a **FAT32** file system. Such pendrives can be used with most operating systems. All this can be done within mkusb, but you can also use ***gparted*** for the partitioning.

But if you want to store files bigger than 4 GB, you should have another file system. If you want to use it with linux and windows, you can use the NTFS file system. If you intend to use it only with linux, you can use the linux file system ext4.

---

### Post by lynx6 on 2016-03-23
For the pendrive is recognized in File Manager both in Linux and in Windows can be formatted in FAT32?

---

### Post by sudodus on 2016-03-23
The typical file system in USB pendrives is FAT32, and it works in linux, Windows and MacOS. (FAT32 is developed from the old FAT file system used by the DOS operating system (IBM-DOS, MSDOS, DRDOS ...).

[https://en.wikipedia.org/wiki/File_Allocation_Table](https://en.wikipedia.org/wiki/File_Allocation_Table)

> Originally designed in 1977 for use on floppy disks, FAT was soon adapted and used almost universally on hard disks throughout the DOS and Windows 9x eras for two decades. As disk drives evolved, the capabilities of the file system have been extended accordingly, resulting in three major file system variants: FAT12, FAT16 and FAT32. The FAT standard has also been expanded in other ways while generally preserving backward compatibility with existing software.

With the introduction of more powerful computers and operating systems, as well as the development of more complex file systems for them, FAT is no longer the default file system for usage on Microsoft Windows computers.

...

Uses

The FAT file system has a long history (over three decades) of usage on desktops and portable computers, and it is frequently used in embedded solutions.

FAT offers reasonably good performance and robustness, even in very light-weight implementations. It is therefore widely adopted and supported by virtually all existing operating systems for personal computers as well as some home computers and a multitude of embedded systems. As such, it continues to be the most widespread file system worldwide. This also makes it a useful format for solid-state memory cards and a convenient way to share data between operating systems.

FAT file systems are the default file system for removable media (with the exception of CDs and DVDs) and as such are commonly found on floppy disks, super-floppies, memory and flash memory cards or USB flash drives and are supported by most portable devices such as PDAs, digital cameras, camcorders, media players, or mobile phones. While FAT12 is omnipresent on floppy disks, FAT16 and FAT32 are typically found on the larger media.

FAT was also commonly used on hard disks throughout the DOS and Windows 9x eras, but its use on hard drives has declined since the introduction of Windows XP, which primarily uses the newer NTFS. FAT is still used in hard drives expected to be used by multiple operating systems, such as in shared Windows, Linux and DOS environments.

**Due to the widespread use of FAT-formatted media, many operating systems provide support for FAT** through official or third-party file system handlers. For example, OS/2, Linux, FreeBSD and BeOS provide built-in support for FAT, even though they also support more sophisticated file systems such as ext4 or btrfs. Mac OS 9 and Mac OS X support FAT file systems on volumes other than the boot disk. AmigaOS supports FAT through the CrossDOS package.

---

### Post by lynx6 on 2016-03-28
> The typical file system in USB pendrives is FAT32, and it works in  linux, Windows and MacOS. (FAT32 is developed from the old FAT file  system used by the DOS operating system (IBM-DOS, MSDOS, DRDOS ...).

Okay, I understand now.
Thank you very much.

---

### Post by sudodus on 2016-03-28
> **lynx6 said:**
> Okay, I understand now.
Thank you very much.

You are welcome :-)

---

