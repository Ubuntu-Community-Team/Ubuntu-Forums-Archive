---
title: "Windows update disables automatic mount of drives"
date: 2007-07-14
forum: General Help
---

### Post by cristian_orem on 2007-07-14
I have a dual boot setup (WinXP and Ubuntu) with several hard drives (NTFS and FAT32) both of which I have been able to read, and write from linux (with the automatix NTFS automount.)
Just a few days ago I was booted into windows to play Day of Defeat when I noticed some updates had been automatically installed - after the computer rebooted itself (arghhh) I was unable to read any of the drives I setup to automatically mount in Ubuntu. So, I ran a system restore in windows, and now I can read them again.
I just wanted to throw this out there for anybody else having the same problem.
I'm not sure which update it is exactly, but it is one of the latest ones.

---

### Post by earobinson on 2007-07-14
let me just make sure I understand this, if you do a windows update you can not read the partitions in linux?

---

### Post by cristian_orem on 2007-07-14
> **earobinson said:**
> let me just make sure I understand this, if you do a windows update you can not read the partitions in linux?

I believe so, after the update I tried to mount the drives manually, and with the gnome partition editor (not sure if thats the best way to do it) and had no luck. A system restore in windows to before the updates were ran fixed it (the partitions were mounted automatically and work.)

---

### Post by earobinson on 2007-07-14
you could try this and let us know how it goes
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

But I think its a bug, you could file a bug report

---

### Post by cristian_orem on 2007-07-14
> **earobinson said:**
> you could try this and let us know how it goes
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

But I think its a bug, you could file a bug report

Thanks, but I already fixed it by removing the windows updates. I just wanted to throw this out there for anybody else having the same problem

---

### Post by earobinson on 2007-07-14
Ya I relised you fixed it, If it comes up again you could still try that, not updating your computer IMHO is a bad idea.

---

