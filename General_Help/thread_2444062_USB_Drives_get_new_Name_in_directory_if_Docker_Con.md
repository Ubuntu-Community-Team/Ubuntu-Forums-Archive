---
title: "USB Drives get new Name in directory if Docker Container isn't stopped first"
date: 2020-05-24
forum: General Help
---

### Post by brimcgon on 2020-05-24
I have two USB drives named SSD500 and Backups.  These names are what usually comes up automatically when I boot Ubuntu.  If, however, i have my Jellyfin container running in Docker when I reboot, then there will be two empty directories named SSD500 and Backups, the actual drives will be assigned to directories SSD5001 and Backups1.  This is all in /media/brian/ btw. 

I then have to play this silly game of unmounting the drives, deleting the empty directories, then remounting the drives, and sometimes I have to do it a couple of times before it gives them the original names again.   

Is there something I can do so when the machine shuts down or reboots I can first stop Jellyfin without having to manually remember to do it?

---

