---
title: "How to take ownership of a new partition?"
date: 2007-09-30
forum: General Help
---

### Post by MegaSvensk on 2007-09-30
Hi,

I just created a new ext3 partition on my external hard drive (using Paragon Partition Manager in Win XP) but the ownership is set to root so I cannot do anything with it.
How do change the ownership?

I found this command in another thread on this topic but nothing happened when I ran it.
sudo chmod -R 777 /media/yourHardrive

---

### Post by glotz on 2007-09-30
man chmod :)

---

### Post by isecore on 2007-09-30
First off you need to mount it. Unless it's automatically mounted, of course. However they seldom are.

The best place to mount it is in /media. Make a new directory there, something that signifies the disk. I have for example my 200 gig drive mounted in /media/200gig. You'll have to create this directory using the sudo command in a terminal, and afterwards you have to change the ownership from root to your own user, again with the sudo command.

For example, this is how you change ownership of a directory called /media/harddrive:

```
sudo chown username:usergroup /media/harddrive
```

Then you mount the partition, in this example I assume that it's the first partition on the second device in the IDE-chain and we want to mount it in /media/harddrive:

```
sudo mount /dev/hdb1 /media/harddrive
```

To make sure it's mounted on each boot you have to edit the /etc/fstab file. Again, this has to be done as root. I.e.:

```
sudo nano /etc/fstab
```

Insert something similar to this code, of course replacing everything with the proper device, mount point and filesystem type:

```
/dev/hdb1 /media/harddrive ext3 defaults,errors=remount-ro,users,user_xattr,user 0 0
```

After that, just do ```
sudo mount /media/harddrive
```

This is a kinda old-school way, but this is how I do it. Just make sure you keep a backup of the fstab file in case you fubar something.

---

### Post by MegaSvensk on 2007-09-30
It is mounted because it shows up on the desktop.

I'll try doing the stuff you wrote.

How do I find out what dev/whatever name my partition have?

Is there a more "new-school" way of doing it? Because I'm new to Linux and I'm afraid i'll mess something up.

---

### Post by Irihapeti on 2007-09-30
```
sudo fdisk -l
```

will give you a list of your partitions. Assuming you know the size of the partition you created, you should be able to identify it.

---

### Post by MegaSvensk on 2007-09-30
I did the chown-thing and now I have ownership.

Thanks for your help.

---

### Post by BoardDWorld on 2007-10-23
Thank you kindly for this tutorial isecore, it worked out well.

---

