---
title: "Make a new data partition to store Android Studio files"
date: 2017-10-13
forum: General Help
---

### Post by airilsra on 2017-10-13
My current Ubuntu 16.04 install is running out of space, and Android Studio is the one which take the big chunk of it.

I have an unused 30GB partition, which I plan to be the new location for Android Studio files. I've checked that I can move those files within Android Studio settings.

My question is:

1. What partition format should I use?
2. Regarding setting correct permissions, what additional tasks should I do after creating the partition, where should I mount it, etc?
3. For automounting the partition should I add the partition to /etc/fstab or mount it at login by adding udisksctl command to Startup Applications? Currently I'm using the latter for a couple of data partitions I have.

Edit: I went ahead and did what I wanted to do. Here the steps I chose:
1. I use ext4.
2 and 3. 
After the partition was created and then mounted I changed the owner of the mount directory to myusername:mygroup.
For automount method I use udisksctl that I set on custom startup applications.

After that I copied Android Studio sdk folder to said new partition. And then change the settings from within Android Studio.

---

