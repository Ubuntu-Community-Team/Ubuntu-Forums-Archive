---
title: "slow boot"
date: 2016-12-23
forum: General Help
---

### Post by hyburn on 2016-12-23
systemd-analyze
Startup finished in 4.870s (kernel) + 43.989s (userspace) = 48.859s

36.631s dev-sda1.device

the computer waits for something to time out. how can I determine what is needing to time out to fix it?

---

### Post by oldfred on 2016-12-23
What is sda1?
Is it trying to run fsck as it is corrupted, but not fixed, so same issue?

Or just an unknown device?

---

### Post by hyburn on 2016-12-23
/dev/sda1  *         2048 279310335 279308288 133.2G 83 Linux <----- boot
/dev/sda2       279312382 312580095  33267714  15.9G  5 Extended
/dev/sda5       279312384 312580095  33267712  15.9G 82 Linux swap / Solaris

---

### Post by hyburn on 2016-12-23
I ran test drive and this is the result. I would assume that my drive is too small

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63

The harddisk (160 GB / 149 GiB) seems too small! (< 214 GB / 199 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                 8636  70 11 26022 105  3  279308288
   Linux                 8639 150 24 26025 185 16  279308288
   Linux                 8640 252 61 26027  32 53  279308288
   Linux                 8646 185 52 26032 220 44  279308288
   Linux                 8646 250 53 26033  30 45  279308288

```

---

### Post by oldfred on 2016-12-23
All those partitions do not look like valid partitions. Testdisk sometimes finds extraneous things.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by hyburn on 2016-12-26
I bought a 2 TB drive today. Re-installed Ubuntu 16.04 and went through all the beginning steps.

now my boot time is just over 16 seconds.

---

