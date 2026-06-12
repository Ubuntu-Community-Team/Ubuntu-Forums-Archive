---
title: "Extracting game CD"
date: 2015-11-12
forum: General Help
---

### Post by UncleMonty on 2015-11-12
I'm attempting to extract the data files from a gaming CD, as the cd drive on my laptop has seen better days, is there any software which is suitable for this?

---

### Post by yancek on 2015-11-12
What game?  Is it designed to run on Linux/Ubuntu?  Check that first.
Does your CD drive work at all?  Otherwise, no way to access it.
You neglected to indicate which operating system you have but since you are posting on a Linux/Ubuntu forum, is that what you have?
If your operating system is functioning properly, you should be able to access the files on the CD by mounting the CD or by looking at it under the /media/username directory, finding the correct UUID.

---

### Post by UncleMonty on 2015-11-15
> **yancek said:**
> What game?  Is it designed to run on Linux/Ubuntu?  Check that first.
Does your CD drive work at all?  Otherwise, no way to access it.
You neglected to indicate which operating system you have but since you are posting on a Linux/Ubuntu forum, is that what you have?
If your operating system is functioning properly, you should be able to access the files on the CD by mounting the CD or by looking at it under the /media/username directory, finding the correct UUID.


Hitman blood money. Yep it runs fine in Wine - I've run it perfectly in the past.
Yep the drive is brand new.
Ubuntu 14.04 (sorry I don't know how I forgot to include that detail - this is what happens when you post whilst under the weather).

---

### Post by yancek on 2015-11-15
If you put the CD in the drive and look in the /media/username directory you should see it.  Either a new UUID or the name of the CD should show.  Substitute your actual username of course.  From the quick online search I did, you need to either run it on wine or maybe playonlinux.

---

