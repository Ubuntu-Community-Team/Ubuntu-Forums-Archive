---
title: "Share a partition between Windows and Linux?"
date: 2013-01-30
forum: General Help
---

### Post by ComradeNF on 2013-01-30
So I need to switch between Windows and Linux a lot so I need access to a partition that I can both read and write to from both operating systems. I currently have Windows 8 installed on one partition and Linux Mint on the other (will be switching to Ubuntu soon but I thought I'd give Mint a try as well).

Does anyone know how I can format such a partition (already have the unallocated space ready to go) so I can store and read/write files from both OSs?

Thanks!

---

### Post by furything on 2013-01-30
If I understand you correctly you plan this
Win 8 on partition x
mint or ubuntu on partition y
shared drive partition z

Have I understood you correctly? If so partition z should be ntfs as windows won't read linux partitions.

However you can always use a simple directory on win 8 partition and use that between both os e.g. c:\work

You can also use fstab config in linux to always mount the extra partition or folder.

---

### Post by ComradeNF on 2013-01-30
> **furything said:**
> If I understand you correctly you plan this
Win 8 on partition x
mint or ubuntu on partition y
shared drive partition z

Have I understood you correctly? If so partition z should be ntfs as windows won't read linux partitions.

However you can always use a simple directory on win 8 partition and use that between both os e.g. c:\work

You can also use fstab config in linux to always mount the extra partition or folder.

Yes, this is exactly what I want. I actually have formatted it to NTFS but for some reason whatever files I place from Windows onto the drive are not visible in Linux, but all files placed inside while in Linux are visible in both Linux and Windows 8. Is there a reason for this?

I formatted the drive as NTFS in both Linux and Windows 8 but this issue still persists. I'm assuming it has something to do with the NTFS filesystem?

Some help would be appreciated!

---

### Post by Warren Hill on 2013-01-30
You could try formatting the drive FAT32.

I have a dual boot system with a NTFS drive for windows only, Two ext4 drives Linux only, one root the other home and a shared FAT32 drive.  Works well.

---

### Post by orb9220 on 2013-01-30
Sounds more like a file permission issue with Win8?

As have Win7,Winxp & Linux pluse 2 external ntfs external usb drives. 

And Linux has access to any files I have saved or created in Win7 or Winxp partitions or any files I have saved to external usb drives as well.

All three OS'es can access any files on ntfs partition. If I wanted to install a program in Windows7 then I could also have access to files on ext4 linux partitions.

Like I said think it has something to do with Windows 8?

As setup has worked with Ubuntu 12.10,Linux Mint 14 Cinnamon & KDE,Fuduntu,Bodhi,Voyager 12.10 xfce.
.

---

### Post by furything on 2013-01-30
Yes agree permissions

In Windows 8 have a look at the default permissions/advanced permissions of the root drive.
Make sure full control for everyone applying to all directories and sub directories (you may have to change permissions on the files you already created)

I am still on 7 so can only assume the security structure is the same.

---

### Post by Rebelli0us on 2013-01-30
Another solution is to run Linux **and** and one or more versions of Windows **simultaneously** as virtual machines (Guests) using VirtualBox. You can do the whole thing in a single partition and share all the files between all running OSes.

Here's one of my machines running Ubuntu, Windows 7 and 2000 simultaneously (no rebooting needed) and all files are shared. Windows can even access the ext4 file system.
[IMG]http://bellsouthpwp2.net/z/w/zw42vcqx9a/temp/Screenshot_50P.png[/IMG]

---

