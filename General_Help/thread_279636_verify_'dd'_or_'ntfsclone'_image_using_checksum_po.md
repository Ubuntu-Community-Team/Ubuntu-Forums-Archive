---
title: "verify 'dd' or 'ntfsclone' image using checksum possible?"
date: 2006-10-18
forum: General Help
---

### Post by mogliii on 2006-10-18
Hi,

I'm trying to install a automated backup solution on the windows xp pc of my father. 

The computer setup is as follow:

2x 60 GB Raid1 (Promise FastTrak100 Lite) with System partition and Documents partition (both NTFS)

1x 120 GB with Linux (Ubuntu 6.06, server, icewm installed) and Files partition (NTFS)

250 GB external harddrive (ext2)

My longterm aim is to install a script that gets started directly after linux boots. The function of the script is:

- write logfile
- backup winxp and documents parition using ntfsclone
- have always two backups, and delete the older one before starting new backup
- verify! the created image.
- shutdown after finishing, noting all results in the logfile (maybe saving to a small fat partition)

And here is my question: How to verify the images i do with ntfsclone (or dd). I tried with cksum, but it doesnt seem to work.

I used the following commands:
```
# dd if=/dev/hde of=/mnt/usb/mbr.bak bs=512 count=1
*note: this will save the master boot record of the harddrive, containing the partition table and so on*

# cksum /mnt/usb/mbr.bak

# dd if=/dev/hde of=/mnt/usb/mbr.bak bs=512 count=1 | cksum
```

The method above gave me different results for the checksum. Can anyone give me an advice how to do this? As the files are backed up automatically at night time is not a problem, but when doing backup, it should be as safe as possible.

All help apreciated. Maybe I will ask for some help again when writing the script. But first of all I want it to work manually.

Also hints on already existing, similar projects would be apreciable. Maybe this idea is not new?!?

---

