---
title: "primary GPT table is corrupt"
date: 2022-12-28
forum: General Help
---

### Post by gus_zernial on 2022-12-28
I have a fresh install of Kubuntu 22.10 on a three disk workstation, with a single NvME SSD as the system disk and two HDDs to be used in an MDADM Raid 1 array to be mounted as my /home (data) disk. On my system SSD and one of my two Raid disks, when I use #fdisk -l I get the warning "The primary GPT table is corrupt, but the backup appears OK, so that will be used". How can I copy the working backup GPT table to the Primary to eliminate the warning?

Thx, Gus

---

### Post by oldfred on 2022-12-28
Make sure you have good backups. 
RAID is for uptime, not backup.
Be careful of the RAID, but gdisk works great on standard drives. 

You can use gdisk.
GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html) & 
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :

---

