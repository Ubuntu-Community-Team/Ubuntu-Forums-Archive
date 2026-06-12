---
title: "mdadm RAID0 Issues"
date: 2012-11-27
forum: General Help
---

### Post by Acer8888 on 2012-11-27
Hello, i am very new to Ubuntu. I have a 60Gig SSD running 10.04 and two 2TB HD in a RAID0 array using mdadm. I found a guide to setup the array and its working great.. for a while. Seems like every other day i have to restart my server because the 4TB RAID array will only show 5% of the data that is on the drives. Once i restart, the array shows 100% of the data on the drives. Im not sure if the array is shutting down due to inactivity and this is fine but an issue because it does not come back up completely. Im am not sure what is happening just my best guess. I am running a MythTV backend on the server, which i know it cannot record my shows sometimes because it cannot access the storage directories on the array. I am using the following as my fstab for the array.Any input would greatly be appreciated.

/dev/md0 /media/raid0 auto defaults 0 0


Thank you in advanced!!

---

