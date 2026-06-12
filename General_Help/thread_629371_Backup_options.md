---
title: "Backup options"
date: 2007-12-02
forum: General Help
---

### Post by daz4126 on 2007-12-02
I've just set up a new laptop and have it exactly how I want it. Now I'm looking for backup options. I've done a bit of digging around and found the following options:

1. Partimage with Knoppix
This seems to be like using Norton Ghost and could work well. It would be nice if it was included on the Ubuntu live CD

2. Simple Backup (from the repositories)
This seems like an easy to use gui, but it only backs up folders. Which folders should I backup and would I be able to choose a list of options that would keep all the software that I've installed?

3. Use the dd command and than tar the folder to compress it
This method was suggested by X0as using a live CD:
```
dd if=/dev/sda1 of=/mnt/backups/sda1-image
```
and to restore:
```
dd if=/mnt/backups/sda1-image of=/dev/sda1
```

This seems quite straightforward, are there any issues with this?

I think that Ubuntu is missing a trick here. If an easy to use backup solution could be incorporated into the live CD then I think it would be incredibly popular with users. As well as this, it could be given out to Windows users as a 'recovery disc' to backup their systems with, instead of using paid for programs like Ghost. They might then realise that the 'recovery program' was actually a full OS that was actually better than the one they were trying to restore!

Any thoughts?

DAZ

---

