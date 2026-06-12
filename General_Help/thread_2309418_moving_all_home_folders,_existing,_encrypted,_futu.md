---
title: "moving all home folders, existing, encrypted, future to a different path"
date: 2016-01-10
forum: General Help
---

### Post by NotQuiteSU on 2016-01-10
I installed Ubuntu Server 14 LTS, opting for the ecrypted home folder. I installed on a small SSD, but I'd like to move it all to a new drive I installed and mounted as /media/disk1. So they would all be under /media/disk1/homes/.

I saw some guides for moving an existing home folder, but I wasn't sure how it would impact encrypted home folders as well as future created home folders.

---

### Post by oldfred on 2016-01-10
I do not think encryption makes a difference, but you need to mount it as /home in its own partition.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You probably need to make sure you have unencrypted the partition before you move it, but not sure. After you copy to the temporary mount you can see if you can manually mount & unencrypt it still.

---

### Post by NotQuiteSU on 2016-01-11
> **oldfred said:**
> I do not think encryption makes a difference,  but you need to mount it as /home in its own partition.

So if I have sdb, and sdb1 is dedicated to the full size of the drive, do i have to repartition to make sdb2?

---

### Post by oldfred on 2016-01-11
What then is sdb1, if you want it can be /home with all your data.

---

