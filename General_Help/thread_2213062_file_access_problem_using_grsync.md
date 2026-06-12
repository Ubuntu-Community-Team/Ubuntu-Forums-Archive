---
title: "file access problem using grsync"
date: 2014-03-24
forum: General Help
---

### Post by DrScum on 2014-03-24
I am trying to use grsync to make an incremental backup to a backup server. I mount the backupserver directory to /home/thunderbird-bak. Thunderbird-bak has file permissions set to 777 recoursively. Grsync is set to synchronize the mounted backup directory with ./thunderbird/userprofile.default. When I start grsync, a directory ./thunderbird is created in the backup directory but grsync fails with the error message: sending incremental file list
userprofile.default/
rsync: recv_generator: mkdir "/home/thunderbird-bak/userprofile.default" failed: Permission denied (13)

apparently grsync cannot write in ./thunderbird 

Here is my question: how do I set up a simple backup procedure where I mount a network drive to my local drive and synchronize the directory and all its subdirectories I want to backup with the mounted network drive. 

I thought I know my way around in ubuntu a little bit, but this simple task seems to be rather complicated.

---

