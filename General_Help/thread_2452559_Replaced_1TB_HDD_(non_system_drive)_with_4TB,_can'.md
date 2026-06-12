---
title: "Replaced 1TB HDD (non system drive) with 4TB, can't use same mount point?"
date: 2020-10-24
forum: General Help
---

### Post by mikeymikec on 2020-10-24
I had a 1TB HDD with an NTFS file system on it.  I replaced it with a 4TB HDD again with NTFS (dual-booting, partitioned and formatted the drive in Win10).  In Lubuntu, if I use the 'use session defaults' option and tell Lubuntu to mount it, it works fine. Using the Disks program, if I tell it to use the same mount point that the 1TB drive used to use (/mnt/data), the Disks program responds:

message recipient disconnected from message bus without replying (g-dbus-error-quark, 4)

dmesg says:
[   82.235290] pool[1468]: segfault at 8 ip 0000562c9c1bfa80 sp 00007f5db58694f0 error 4 in udisksd[562c9c191000+69000]

It would be a PITA to not use the same mount point.  How can I convince Lubuntu to do what I want?

---

### Post by mikeymikec on 2020-10-24
Hum.  After I removed the old entry from /etc/fstab (in hindsight I should have just commented it), rebooted, it mounted the 4TB partition the way I wanted it, though Lubuntu did say 'system problem detected'.  I'll see how that goes.

- edit - it's throwing that error every time, yet mounts the partition seemingly no problem.

---

### Post by oldfred on 2020-10-24
Not sure if this will show anything or not, if sdb or change to your drive:
sudo gdisk -l /dev/sdb

Best to use Windows tools for Windows & Linux tools for Linux.
But I prefer gparted or gdisk for gpt drives.

---

### Post by mikeymikec on 2020-10-25
I should have marked this as solved late last night but I was well and truly done for the day, thanks anyway :)

I got rid of the error with sudo rm /var/crash/*

---

