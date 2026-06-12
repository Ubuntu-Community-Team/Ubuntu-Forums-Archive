---
title: "External USB drive is read-only?"
date: 2008-07-09
forum: General Help
---

### Post by dchurch24 on 2008-07-09
Hi all,

I have an external USB drive that I use for backups - recently I installed vbox and completely stuffed my system up and so did a complete reinstall from scratch.

Not a problem as all my important stuff (pics, music etc...) were backed up to the USB drive.

The drive came pre-formatted as FAT32.

To make sure I had everything I restored a later backup from my laptop to the USB drive before I did a reinstall (call me anal, but I cannot lose my pictures so take extra care of those).

The USB 'drive' has two WD HDDs in it, and I have just created a cron job to move everything over to the 'other' drive in the USB and want to delete everything from the first HDD (where the new backup was).

But for some reason it's read only - I am the owner, yet it will not let me delete anything from that partition.

Thinking that I would just format it and while I was at it change it from FAT32 to ext3, I opened gParted as root.

For some reason in gParted the format option is greyed out so I can do nothing with it at all.

This would also solve my other problem of not being able to delete anything from the Deleted Folder on there too.

Do I have to unmount the drive or anything before I can format it? I tried to do that, but it says the device is busy - which I suppose is understandable as I am currently testing my cron job on the other drive in the USB housing.

---

### Post by scouser73 on 2008-07-09
I've had problems with external HDDs also, and I've found that to gain permissions on a drive where there is no data stored would be to format it to NTFS.

I know that it might not be the solution you actually need but if no other replies come then that is what I would suggest.

---

### Post by chrisccoulson on 2008-07-09
Partitions sometimes get remounted read-only when filesystem errors are detected, in order to reduce the likelihood of further data loss. It would be worth doing the following in a terminal (with the drive disconnected):
```
tail -f /var/log/syslog
```
Now connect the drive and monitor the output in this terminal. If you see anything like 'Filesystem panic', then your drive has errors, which you might be able to fix with dosfsck. 

**You must always unmount a disk before running a checking utility such as dosfsck, or you risk serious data loss** 

To use dosfsck (after unmounting the disks):
```
sudo dosfsck -a -v /dev/sdxx
```
...where /dev/sdxx is the device node for your drive. You might be able to find this from the information that is written in to your syslog when you connect the drive. if you're unsure, then ask. The -a option automatically fixes errors and the -v is for verbose output

---

