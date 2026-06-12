---
title: "Resize partition from within FF 7.04 or from within WIN XP?"
date: 2007-05-19
forum: General Help
---

### Post by intricate on 2007-05-19
I use FF 7.04 and want to reduce the partition size for FF and increase the partition size for Win XP. Both partitions reside on one physical laptop HDD.  Is it better to resize the partitions from the Live 7.04 CD or can I do the same resizing just as well from Windows using a partition manager? What do you recommend?

Thanks you.

---

### Post by mahy on 2007-05-19
I think it's best to use to Gparted to resize the Ubuntu partition and some windows tool to resize the windows one.

---

### Post by public_void on 2007-05-19
I'd use GParted for both Ubuntu and Windows. Its worked fine for me, resizing Ext3 and NTFS.

---

### Post by scradock on 2007-05-19
I'm not sure - Gparted and Partition Magic in WXP don't always play nice with each other. 

I've had trouble several times with one reporting partition errors after I've used the other one, and now I can't resize my Windows partition at all. And I REALLY REALLY want to recover 30 GB of my hard drive to use for Ubuntu. 

Ubuntu (Feisty and Edgy) and WXP all boot and run - but the first primary partition won't resize.

---

### Post by intricate on 2007-05-19
any step by step way to use GParted that I can use?  Thanks!

---

### Post by aldenhg on 2007-05-20
You're not going to be able to resize your Feisty partition while running it. It has to stay mounted and you can't unmount your system partition. What you should do is boot up the liveCD you installed with and use Gparted on /dev/sda. The first thing you should do is resize the Feisty partition (by right clikcing and choosing Resize) to it's new size and then resize the XP partition to fill the space. Make sure you resize the Feisty partition from the left. Hit the apply button and it will do all the rest for you.

---

