---
title: "increase /home directory"
date: 2007-10-28
forum: General Help
---

### Post by dachinster on 2007-10-28
Hi,
I had 3 hard disks recently and was running windows with ubuntu 7.10 dual booted on a separate disk.

The hard drive with Windows on it died recently (clicking noises) and now I have 2 disks and 4 partitions (2 partitions per disk).
Thankfully all my data is backed up.

3 partitions are ntfs and the one with ubuntu on it is 20GB and i would like to increase the file size of my /home directory which resides within the ubuntu partition on the 20GB disk.

Can i use gparted to resize the ntfs partitions safely? 
after i do this, if i format the unallocated, resized space into ext3, and i choose to join the partitions, will it merge into my current 20GB ext3 ubuntu file system without causing data loss?


Other question
also, suppose i resize one of the ntfs partitions and decide to dedicate it for my /home directory, how do i permanently change and point ubuntu to this new /home directory which will exist on another partition/ hard drive?

---

### Post by dachinster on 2007-10-30
bump

---

### Post by Meson on 2007-10-30
I've had some pretty good success with GParted.  I've never really had a major meltdown, and I've split and merged stuff before.

However I !!!ALWAYS RUN A BACKUP!!! before doing anything that could easily result in failure.

---

### Post by dachinster on 2007-10-31
thanks for the response

Now, I have been thinking.
I am going to get another drive, but I want to dedicate it to my /home directory.

How do i change my /home directory from the small partition it is on and migrate it to the new drive so that ubuntu will always access that drive when i click on home?

---

