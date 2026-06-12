---
title: "Rsync to a Box.com WebDAV account takes up space on the local drive in Ubuntu 16.04"
date: 2016-08-17
forum: General Help
---

### Post by joe132q on 2016-08-17
I am using Ubuntu 16.04 on a 256GB SSD, and have three other harddrives mounted to the "/mnt/media/" directory that are used for storage. I tried using Rsync to back up the three harddrives to my box account that is mounted as a WebDAV directory. The problem I ran into was that as the rsync process was running, it would start to fill up space on the SSD running the OS, while at the same time uploading the files to Box. Eventually it only left around 30GB of space on the SSD before I noticed what was going on.

This is the command that I ran:

sudo rsync -hva "/mnt/media/Data Folder 1" "/mnt/media/Box Folder"

Is it normal for it to take up space like that? Also, how do I reclaim that space? Is there a folder that holds the files "temporarily" that I can go to and remove to free up the space again?

Thanks!
Joe

---

