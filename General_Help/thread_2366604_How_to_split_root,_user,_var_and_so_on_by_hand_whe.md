---
title: "How to split root, user, var and so on by hand when installing?"
date: 2017-07-19
forum: General Help
---

### Post by patrikmellq on 2017-07-19
Hello i am about installing Ubuntu Mate on SD card.
I have Ubuntu Mate on a USB stick and will install it on my SD card as working distro.

Now it ask how to format the SD card, the size is 16 GB

/boot
/root
/home
/usr
/usr local
/temp
/var
/opt
/swap

Do i need all or can i only use

 /boot 
/swap 
/root

What size should each one have

Thanks for the help.
Note i have to pick option "Other" when installing to my SD card with USB converter attach to it - so i can not automate the process installing and format by it self.

---

### Post by cariboo on 2017-07-19
I wouldn't bother on a 16GB SD card. Even if installing on a hard drive I wouldn't bother, I usually set up a 20GB partition for / and as much as I feel I need for /home.

As of 17.04 you don't even need a swap partition.

---

### Post by oldfred on 2017-07-19
On a 16GB flash drive I installed / (root) as 8 GB and 8 GB as just another partition for data. No swap as I have enough RAM that it almost never uses swap. But this was primarily for emergency boot, not daily use.

You could just have / as all 16GB.
Do not make lots of system partitions.

---

### Post by CatKiller on 2017-07-20
Also, to the OP, be aware that /root and / (which is sometimes pronounced "root," because it's the root of the filesystem tree) are entirely different things. You will need a / partition. Almost no one ever needs to do anything with /root (which is simply the root user's Home folder).

---

### Post by vocx on 2017-07-20
> **CatKiller said:**
> Also, to the OP, be aware that /root and / (which is sometimes pronounced "root," because it's the root of the filesystem tree) are entirely different things. You will need a / partition. Almost no one ever needs to do anything with /root (which is simply the root user's Home folder).
Well said.

There is only one partition required which is "/" forward slash, pronounced "the root partition". Every other partition is optional, and depends on your requirements.

Actually there is a distinction between "partitions" and "mount points". A partition is the actual division of the hard drive, and the mount point is how it looks to the operating system (the actual name of the directory). So, you need at least one partition, and that partition must be "mounted" as "/", the root of the file system tree.

The way Linux works, each directory is attached to the root "/" of the tree. Each individual directory could be in a separate partition, but it would be crazy if it were commonly done like that. Usually, you only need one or two additional partitions, to separate physically from the partition containing root "/".
```

/  #main sda1
    /home   #partition sda2
    /root
    /usr
         /local
...

```

I think most new users should not complicate their lives, and just assign most space for "/". Talking specifically about 16 GB, there is not much need to create multiple partitions in such relatively small space. Of course, I would have a separate SD card, USB memory, or external hard drive available to hold personal files if the space is filling fast.

For a large hard disk, say, 128 GB and bigger the user can easily give half to "/" and half to "/home". In fact, i think there is really no necessity to give the root "/" more than 100 GB of space. Most installed programs will probably fit well in that. Anything additional may well be personal files, so can be used for "/home". For instance, I have a root "/" of 19 GB, and it's actually pretty full at 80% use. Maybe I should have created it initially with more room. On the other hand, my "/home" is 180 GB with 40% use.

Creating partitions is useful if you don't want to lose files while reinstalling, so really, the only partition that you would need beside "/" is "/home". Every other directory "/etc", "/usr", "/temp", "/var", etc. will probably be erased in a reinstall, so there is no need to keep it in a separate partition.

---

### Post by Impavidus on 2017-07-22
> **vocx said:**
> Well said.

There is only one partition required which is "/" forward slash, pronounced "the root partition". Every other partition is optional, and depends on your requirements.
Some partitions are actually forbidden. Roughly speaking, the parts of the file system that must be available to fix your system in single user mode or are needed early in the boot process must be on the root partition. That means /root, /bin, /sbin, /lib and /etc.

> 
For a large hard disk, say, 128 GB and bigger the user can easily give half to "/" and half to "/home". In fact, i think there is really no necessity to give the root "/" more than 100 GB of space. Most installed programs will probably fit well in that. Anything additional may well be personal files, so can be used for "/home". For instance, I have a root "/" of 19 GB, and it's actually pretty full at 80% use. Maybe I should have created it initially with more room. On the other hand, my "/home" is 180 GB with 40% use.
It depends on what you want to install and some programs come with a lot of data files (usually in /usr/share/), but it's uncommon to need much more than 15GB on your root partition if you have a separate /home partition (or something equivalent on a server). But if you've hard disk space to spare, it's not really important.

---

