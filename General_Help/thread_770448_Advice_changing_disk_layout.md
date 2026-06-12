---
title: "Advice changing disk layout"
date: 2008-04-27
forum: General Help
---

### Post by DanTidswell on 2008-04-27
Hi

I've installed Hardy Heron using the default disk layout on a clean 250GB drive. I have one large 227GB ext3 for the OS and user-data and a 5.6GB swap drive.

I have everything installed and working great with MythTV and LXBMC and all my devices working perfectly.

Now I would like change to the disk layout to separate the OS from my user data. From what I gather the best way to achieve this is to boot from a CD and resize the main partition and then create an additional partition for the user data in the space I've created.

My question is what is the best way to achieve this?

So far I have:

- Boot from a CD and resize the OS partition to 20GB

- Create a new 'userdata' partition (ext3?)

- Move my home folder to 'userdata' partition (how do I do this?)

- Tell MythTV to save its data on the 'userdata' partition

---

### Post by ghost_ryder35 on 2008-04-27
best way would be to copy your data to a dvd or external hard drive, create the new partition and then copy the data from the external hard drive or dvd on to the new /home directory
```

cp /home /media/your backup media

```

---

### Post by DanTidswell on 2008-04-27
Thanks ghost_ryder35

After I've moved my home folder to the new partition how do I tell the OS to save my data to that folder by default? Does Ubuntu have user profile defaults store somewhere?

Also, once moved can I safely delete the home folder from my OS boot volume?

Thanks,

Dan

---

