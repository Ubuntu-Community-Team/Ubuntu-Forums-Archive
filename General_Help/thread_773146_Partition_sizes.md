---
title: "Partition sizes?"
date: 2008-04-28
forum: General Help
---

### Post by patrickaupperle on 2008-04-28
I am going to install sidux (can't get my computer to upgrade to hardy) over my ubuntu install. I want to use a separate home partition this time. How big  should I make these partitions? I have a 60 GB drive.

---

### Post by pjkoczan on 2008-04-28
> **patrickaupperle said:**
> I am going to install sidux (can't get my computer to upgrade to hardy) over my ubuntu install. I want to use a separate home partition this time. How big  should I make these partitions? I have a 60 GB drive.

Ultimately, that's up to you. However, you should always allow some wiggle room for the partitions to grow should you ever decide to install a lot more software or such.

It looks like you're using just 3 GB for stuff other than /home. I'd say that
10 GB (swap partition included) for non-home stuff is reasonable, but again, it's your system, and ultimately you have the best judgment on the matter.

Of course, you can always use something like parted to resize your partitions later, but be careful when doing so and read manuals since disk block management is potentially dangerous.

Hope this helps.

---

### Post by evozniak on 2008-04-28
aways i use 10gb for / and rest for /homee

---

### Post by patrickaupperle on 2008-04-28
> **pjkoczan said:**
> Ultimately, that's up to you. However, you should always allow some wiggle room for the partitions to grow should you ever decide to install a lot more software or such.

It looks like you're using just 3 GB for stuff other than /home. I'd say that
10 GB (swap partition included) for non-home stuff is reasonable, but again, it's your system, and ultimately you have the best judgment on the matter.

Of course, you can always use something like parted to resize your partitions later, but be careful when doing so and read manuals since disk block management is potentially dangerous.

Hope this helps.

Thanks. I don't quite know what your saying about the disk block management, though.

---

### Post by pjkoczan on 2008-04-29
> **patrickaupperle said:**
> Thanks. I don't quite know what your saying about the disk block management, though.

I mean that using fdisk or parted or some other disk partition manager could result in overwriting or erasing data if you're not careful.

Sorry if I was unclear before.

---

### Post by patrickaupperle on 2008-04-30
> **pjkoczan said:**
> I mean that using fdisk or parted or some other disk partition manager could result in overwriting or erasing data if you're not careful.

Sorry if I was unclear before.

Oh, thank you for clarification. Good thing I am keeping backups. :)

---

