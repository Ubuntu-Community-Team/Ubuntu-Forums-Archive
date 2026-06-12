---
title: "Help resizing partitions"
date: 2014-01-14
forum: General Help
---

### Post by lordnicho1 on 2014-01-14
Hi i cant add any more space to a partition i got like 60gb that dosent belong anyway but i cant add them to a partition. Even when i have ''unlocked'' the partition where i want the space to go but i cant add them. The meter box thingy where you add more memory is on max. Plz help and fast!

---

### Post by tgalati4 on 2014-01-14
Open a terminal and post the output of:

```
sudo fdisk -l
```

And fast!

---

### Post by lordnicho1 on 2014-01-14
i think im getting a error Partition 1 does not start on physical sector boundary.

---

### Post by lordnicho1 on 2014-01-14
When i open the Gparted i want to make a one partition on like 4 diffrent allocated spaces

---

### Post by lordnicho1 on 2014-01-14
But i cant add them all to one allocated space

---

### Post by Bucky Ball on 2014-01-14
What release you are using. To create partitions and resize existing ones everything needs to be unmounted. Boot from Live media (the install disk or USB), 'Try Ubuntu' and when at a desktop launch Gparted and do what you like.

A tip for the future: You have a much better chance of getting help fast by using a descriptive thread title that actually tells us something about your problem. Generic titles like 'Help fast' mean nothing and can put some people off. To be honest, from your post I see nothing that needs fixing fast. It appears you simply want to re-partition your drive.

Most people here need help fast so you are giving us nothing to work with. Also, include as much relevant information as you can, particularly about what your issue is and what you've tried to do to fix it. ;)

---

### Post by lordnicho1 on 2014-01-14
Im using the lastest stable version of ubuntu and i will try that and keep that in mind in the future, thx

---

### Post by Old_Grey_Wolf on 2014-01-14
In post #2 above, tgalati4 tried to help you fast; however, you didn't provide the result from the command.

---

### Post by tgalati4 on 2014-01-15
I wanted to see the current layout of the partitions.  I presumed that there were "holes" of empty space scattered throughout the drive.  You can't simply add them to existing partitions.  You need to delete all of the partitions to the "right" of the empty space, then you can add that space to the partition to the "left".  The sector boundary error is usually minor and can be fixed in gparted, but you have to have a plan on how to lay out the disk.  Part of that plan is to understand how the current partitions are laid out--hence the command to share that with us who are trying to help.

Linux requires one to focus.

---

### Post by oldos2er on 2014-01-15
Changed thread title to something a bit more appropriate.

---

