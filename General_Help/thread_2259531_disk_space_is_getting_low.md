---
title: "disk space is getting low"
date: 2015-01-05
forum: General Help
---

### Post by metaldefektor on 2015-01-05
I have moved everything that I could find out of the /home and when I go into the file system as root and into the temp folder I cannot find any files that can be removed-
I started with 20 out of 45GB used right after install and 2 weeks later there is 40 out of 45 gigs used and I can't find where all this space is being taken up.
New to ubuntu- I'm using Kubuntu 14.02
Many thanks and loving it~

---

### Post by nerdtron on 2015-01-05
let's see how big each folder on the files system.
Post th output of:
```
df -Th
sudo du -sch /* 
```

---

### Post by coldraven on 2015-01-05
> I started with 20 out of 45GB used right after install
That is not normal, a typical install should be about 4GB plus maybe 2GB for the swap partition.
Is is possible that you have an old unused partition left on the drive?
Run this command and post the results here:
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

---

