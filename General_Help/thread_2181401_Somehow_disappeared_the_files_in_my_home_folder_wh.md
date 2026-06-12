---
title: "Somehow disappeared the files in my home folder while attempting to setup NFS"
date: 2013-10-17
forum: General Help
---

### Post by p4lmtree on 2013-10-17
Ubuntu 13.04 and Crunchbang Waldorf

I had been unsuccessfully editing and re-editing my /etc/fstab file trying to make my Ubuntu desktop share files over the network to my Crunchbang netbook. I followed all the directions in the Ubuntu documentation, but nothing worked.  During one of my many "let's reboot and see what happens," I got an unexpected result upon startup: My desktop looked default.  The wallpaper and dock icons were default; Chrome and Firefox thought it was my first time using them (welcome pages, query to set default browser, etc.); all my Music, Pictures,  Documents, and Videos were gone. (interesting side note about the web browsers:  all my add-ons were still installed and enabled, but they didn't work.  Disabling and Re-enabling did nothing; I had to reinstall each one to get them working again)

I have a lot of extra HDD space, so I thought maybe I somehow sent the files to another drive, but they all look normal.  I looked at the size of used space in each partition, and they seem normal. Someone recommended I boot into a live session and try to mount my partitions manually to inspect each one for the newly hidden files.  I may have done it incorrectly, but all I know is that I didn't see anything out of the ordinary ( plus my permission to enter the directory was denied, since the "live" user isn't my actual user ).

All I know is that I never deleted any files.  The only two config files I even touched were /etc/fstab and /etc/exports.  I have since reverted both config files back to default (except for fstab, which still handles my other mounting needs, e.g. mounting /home on an HDD while leaving / on the SSD ).

I'll post any Terminal output you need.  Please help!

df -hT :

```
Filesystem          Type      Size  Used Avail Use% Mounted on
/dev/sda6           ext4      114G   42G   66G  39% /
none                tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs               tmpfs     796M  1.1M  795M   1% /run
none                tmpfs     5.0M     0  5.0M   0% /run/lock
none                tmpfs     3.9G  1.8M  3.9G   1% /run/shm
none                tmpfs     100M   44K  100M   1% /run/user
/dev/sdc1           ext4      928G   22G  859G   3% /home
/dev/sdb1           ext4      1.4T   17G  1.3T   2% /media/me/storage
/home/me/.Private ecryptfs  928G   22G  859G   3% /home/me
/dev/sdb2           fuseblk   489G  135G  354G  28% /media/me/WinStorage
/dev/sda1           fuseblk   116G   68G   48G  59% /media/me/4F0D29E11D7FB65F
/dev/sdc2           ext4      906G   72M  860G   1% /media/me/ea24b5f1-8325-42f2-9eca-07a72f77a6be
```

---

### Post by varunendra on 2013-10-18
> **p4lmtree said:**
> ..During one of my many "let's reboot and see what happens," I got an unexpected result upon startup: My desktop looked default.  The wallpaper and dock icons were default; Chrome and Firefox thought it was my first time using them (welcome pages, query to set default browser, etc.); all my Music, Pictures,  Documents, and Videos were gone. (interesting side note about the web browsers:  all my add-ons were still installed and enabled, but they didn't work.

In short, you seem to have lost your previous Home directory, and now mounting a fresh one, thus losing all the data and configuration. How were you editing the fstab file? If using a GUI editor like gedit, the last version of it would still be there, hidden, as "fstab~". Check it with "View hidden files" enabled and see if it is there.

And do you have an encrypted Home since beginning? Please post the outputs of -
```
cat /etc/fstab
cat /etc/fstab~
sudo fdisk -l
mount
du -h /home/me 2>/dev/null | sort -rh | head -20
```

---

