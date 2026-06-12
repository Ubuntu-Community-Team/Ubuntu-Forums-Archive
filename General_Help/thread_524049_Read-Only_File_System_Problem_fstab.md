---
title: "Read-Only File System Problem fstab"
date: 2007-08-12
forum: General Help
---

### Post by tuxedobuford on 2007-08-12
Hello All,

I've done something incredibly stupid and have tried everything that I"ve found in the forums but have had no luck. I was trying to mount a NTFS drive on my Dapper LTS server and have managed to turn my system to a read-only system. Perhaps because hde1 might now appear to look like an NTFS drive. Anyhow, when I try to edit fstab with vi, it tells me that the file is read only. I've also tried with Knoppix to edit fstab but have had no luck getting past the file permissions.

the line in fstab that is giving me trouble is
 /dev/sda1   /   ntfs-3g defaults

It appears that I screwed up the mountpoint and it's mounting as ntfs drive as root but the drive is no longer connected

Can anyone tell me how to edit fstab and save it if the drive appears to be read only? 

Thanks much

---

### Post by merlinus on 2007-08-12
Did you try:

```

sudo nano /etc/fstab

```

-merlin

---

### Post by tuxedobuford on 2007-08-12
yes, I have no trouble editing fstab with nano or vi but I cannont save the file due to it being "read-only" like everything else on the drive.

---

