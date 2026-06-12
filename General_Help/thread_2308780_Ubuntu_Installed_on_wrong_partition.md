---
title: "Ubuntu Installed on wrong partition"
date: 2016-01-05
forum: General Help
---

### Post by maciej23 on 2016-01-05
Ok, so I make a dumb mistake. I installed Ubuntu on the wrong partition, and by that I lost a lot of important data. What can I do to recover at least some of the lost data?

---

### Post by leunam12 on 2016-01-05
Stop using that disk immediately, then boot a live session from USB or DVD and use a data recovery program to help you recover as much as possible.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Mark Phelps on 2016-01-05
> **maciej23 said:**
> Ok, so I make a dumb mistake. I installed Ubuntu on the wrong partition, and by that I lost a lot of important data. What can I do to recover at least some of the lost data?

If the partition your overwrote contained Windows, you will get better results using Windows data recovery apps than Linux apps.

But to do that, you need to do the following:
1) Remove the drive from your current PC
2) Connect the drive, using an adapter, to a working Windows PC
3) Download and install Active@File Recovery Pro
4) Run the app, point to the drive you want recovered, and choose the option for quick analysys
5) That will create something that resembles the original filesystem on that drive.  Navigate to the folders you want to see if the files are there and have sizes other than Zero.  
6) If they do, go online and purchase a license to do the data recovery.

Good Luck

---

