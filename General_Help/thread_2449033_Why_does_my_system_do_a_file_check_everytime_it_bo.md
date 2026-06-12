---
title: "Why does my system do a file check everytime it boots up"
date: 2020-08-18
forum: General Help
---

### Post by xendistar2 on 2020-08-18
I have a new install of xubuntu 20.04 on my laptop (Lenonvo T530) which I also fitted a new SSD too.

Everytime the laptop boots up it come up and the bottom of the screen checking file system press ctrl-c to cancel

The progress bar is normally at 95% when it appears waits a couple of seconds, completes and the screen changes and says at the top of the screen that sda1 is clean

The SSD has SDA1 (root), SDA2 (home) SDA3 (swap) and an there is an external USB hard disk which is SDB1

Any thoughts?

---

### Post by TheFu on 2020-08-18
File systems that are not closed correctly 
or
when the journal isn't empty 
or
when the number of configured times since the last fsck ran expires
will cause the fsck to be run at boot.

If the system is being shutdown cleanly, then some sort of HW failure is where I'd look.  dmesg and smartctl

---

### Post by xendistar2 on 2020-08-18
I simply click shutdown and its shutdowns.
I have checked dmesg and found nothing un-towards in there.
Check smartctl and ran a long test, no errors reported
I checked the syslog but found nothing relevant to failed shutdown or other failures

---

### Post by TheFu on 2020-08-18
Thanks for that.  Which file systems are being used?
To see only the interesting stuff:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
```
Please post wrapping the output in  'code tags' - that's in the Advanced editor (#) here.  It will ensure the columns line up so the output is readable. Without it, too much hassle to read.

---

### Post by xendistar2 on 2020-08-19
Here is the output

```
mit@telstar:~$ df -hT -x squashfs -x devtmfsFilesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs  3.8G     0  3.8G   0% /dev
tmpfs                       tmpfs     765M  1.8M  763M   1% /run
/dev/sda1                   ext4       45G  7.4G   36G  18% /
tmpfs                       tmpfs     3.8G  454M  3.3G  12% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs     3.8G     0  3.8G   0% /sys/fs/cgroup
/dev/sda2                   ext4       78G   28G   46G  38% /home
/dev/sdb1                   ext4      916G   27G  843G   4% /media/backup
192.168.1.150:/volume1/Data nfs4      1.8T  644G  1.2T  36% /media/nas
tmpfs                       tmpfs     765M   12K  765M   1% /run/user/1000
```

---

### Post by Dennis N on 2020-08-19
the **fsck** utility runs automatically at startup. A status flag in each filesystem superblock is read by fsck before mounting. If not flagged as clean, fsck will try and make repairs. Otherwise, mounting takes place. This repeats for each file system that's to be mounted in fstab.

Sometimes you see output like:
clean, 537061/1794048 files, 4625687/7168000 blocks
which reports status.

A file system is only flagged 'clean' if it was unmounted properly from the previous mount.

---

### Post by maglin2 on 2020-08-19
Just to record a 'me too', I see the file system check message on almost every startup on one of my 'new' machines (less than a year old) running vanilla ubuntu 20.04.
It seems to add negligible time to overall boot, and there are no other issues present, so I've not followed it up. I'll get out the OP's thread now.

---

### Post by TheFu on 2020-08-19
So much for copy/paste of valid commands.  Whatever.

We see you aren't out of space, are using legacy BIOS boot, and ext4 file systems.  For ext4, there is a tune-able parameter for how often a file system gets checked periodically.  I think the default is ... let me check ... 
```
$ sudo tune2fs -l  /dev/vgubuntu-mate/root |grep -i check
Last checked:             Sat May  2 14:02:23 2020
**Check interval:           0 (<none>)**
Checksum type:            crc32c
Checksum:                 0xc5ee9fbd
```

I'm thinking May 2nd is when I installed this 20.04 Mate system.  Looks like the systemd guys are ignoring the tune2fs specified interval for when an fsck should be performed on a clean file system.  
```
$ journalctl -b |grep -i fsck
Jul 26 10:14:16 regulus systemd[1]: Created slice system-systemd\x2dfsck.slice.
Jul 26 10:14:16 regulus systemd[1]: Listening on fsck to fsckd communication Socket.
Jul 26 10:14:20 regulus systemd-fsck[556]: /dev/mapper/vgubuntu--mate-home: clean, 297294/786432 files, 1629973/3145728 blocks
Jul 26 10:14:21 regulus systemd-fsck[591]: fsck.fat 4.1 (2017-01-24)
Jul 26 10:14:21 regulus systemd-fsck[591]: /dev/vda1: 293 files, 1808/130812 clusters
Jul 26 10:14:52 regulus systemd[1]: **systemd-fsckd**.service: Succeeded.
```
Oddly, there 3 file system - root, home, and boot which should each have been treated the same, yet only home and boot got checked. Would be nice if the systemd guys actually followed the configurations for things and didn't decide "that's the old way, we know better", all the time. They don't treat some fstab entries the same too and clearly removed the extremely helpful **sudo touch /forcefsck** technique for forcing an fsck at next boot. Now we get to use grub or some emergency mode to do that on a non-booting system.

July 26 was the last time the machine was rebooted.
```
$ uptime 
 08:12:14 up 23 days, 21:58,  1 user,  load average: 0.00, 0.00, 0.00

```

---

