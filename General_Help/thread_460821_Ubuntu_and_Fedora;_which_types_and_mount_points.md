---
title: "Ubuntu and Fedora; which types and mount points?"
date: 2007-06-01
forum: General Help
---

### Post by Hoffmann on 2007-06-01
Hi,

I am using the Ubuntu live CD to installing Ubuntu. My goal is to have a dual boot with both Ubuntu and Fedora. My question is which mount points  and types should I use for each of those Linux distroes? When I use for both the type "ext3" and mount point "/", I get a error that says that I cannot have both partitions with the same mount point ("/"). So, if I choose ext3 and "/" for Ubuntu, what about for Fedora?

Thanks a lot!

---

### Post by poppers1957 on 2007-06-01
I do not know the answer to your question.  I have fedora core 6 on another hard drive.  It has been my experience that to load 2 on one disk, even if it is Windoze, you will run into problems.  I remove all other hard disks and load any distro alone.  After I am finished, I hook them all back up and change what HD to boot from in the BIOS.  It for me is simpler, and more secure.  I password the BIOS so no one else can change anything there, but you wouldn't have to.  

The reason I do it this way is because, any boot loader will eventually screw up.  I have never had a problem booting this way.  I suggest using a separate HD to all the people I put Linux on for.   

But if you have to do it with one HD, doesn't fedora ask if you want to let it figure it for you?    I am sure someone will post the proper way to partition it for you, but please consider a separate HD.  Will save some grief down the road.

---

### Post by poppers1957 on 2007-06-01
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This is an ISO of a CD to format for Linux.  Just be very careful not to use the windoze partiton.

---

### Post by Hoffmann on 2007-06-01
Thanks you both for reply!
But what about the types and the mount points?
I already partitioned my HD with the Ubuntu live CD.

---

### Post by mcduck on 2007-06-01
In Ubuntu: Ubuntu's root as /, fedoras root as /media/fedora, for example.
In Fedora, Fedora's root as /, Ubuntu root as /media/ubuntu.

That's how I'd do it. Or, alternatively, if you don't want to see the Fedora partiton on your desktop mount it into /mnt/fedora instead.

It's pretty much up to you where you want to mount the other distro's partition.

Type of course depends on what type your partitions are. Most likely both are Ext3.

---

### Post by Hoffmann on 2007-06-01
> **mcduck said:**
> In Ubuntu: Ubuntu's root as /, fedoras root as /media/fedora, for example.
In Fedora, Fedora's root as /, Ubuntu root as /media/ubuntu.

That's how I'd do it. Or, alternatively, if you don't want to see the Fedora partiton on your desktop mount it into /mnt/fedora instead.

It's pretty much up to you where you want to mount the other distro's partition.

Type of course depends on what type your partitions are. Most likely both are Ext3.

Hi mcduck,

I just installed Ubuntu, and now I am trying to install Fedora. I decided to use /mnt/fedora as the Fedora mount point. However, I got the error that says that I didn't defined a root partition, required to install Fedora.

What am I missing?

Thanks!

---

### Post by mcduck on 2007-06-01
> **Hoffmann said:**
> Hi mcduck,

I just installed Ubuntu, and now I am trying to install Fedora. I decided to use /mnt/fedora as the Fedora mount point. However, I got the error that says that I didn't defined a root partition, required to install Fedora.

What am I missing?

Thanks!

Both distributions handle their partitions indipendently of the other.When installing  both need to get a / partition of their own. So, when you install Fedora you need to give it a root parttion with / as mount point. But this is not the same root partition Ubuntu has. Then, in Ubuntu, you can set Ubuntu to mount fedora's root partition into /mnt/fedora. (and in Fedora, set it to mount Ubuntu's root into /mnt/ubuntu).

To make it more clear I'll give examples, imagine that you have a hard disk called sda,with 3 partitions, sda1 for Ubuntu, sda2 for Fedora and sda3 is swap. Then in Ubuntu you mount sda1 into /, sda2 into /mnt/fedora and sda3 as swap. In Fedora, you set sda2 as /, sda1 as /mnt/ubuntu and sda3 as swap.

Ubuntu:
```
sda1  /
sda2  /mnt/fedora
sda3  swap
```

Fedora:
```
sda1  /mnt/ubuntu
sda2  /
sda3  swap
```

---

### Post by Hoffmann on 2007-06-01
> **mcduck said:**
> Both distributions handle their partitions indipendently of the other.When installing  both need to get a / partition of their own. So, when you install Fedora you need to give it a root parttion with / as mount point. But this is not the same root partition Ubuntu has. Then, in Ubuntu, you can set Ubuntu to mount fedora's root partition into /mnt/fedora. (and in Fedora, set it to mount Ubuntu's root into /mnt/ubuntu).

To make it more clear I'll give examples, imagine that you have a hard disk called sda,with 3 partitions, sda1 for Ubuntu, sda2 for Fedora and sda3 is swap. Then in Ubuntu you mount sda1 into /, sda2 into /mnt/fedora and sda3 as swap. In Fedora, you set sda2 as /, sda1 as /mnt/ubuntu and sda3 as swap.

Ubuntu:
```
sda1  /
sda2  /mnt/fedora
sda3  swap
```

Fedora:
```
sda1  /mnt/ubuntu
sda2  /
sda3  swap
```

After installing Fedora, I ONLY can boot to Fedora. Any suggestions?
Thanks, again.

---

### Post by mcduck on 2007-06-01
> **Hoffmann said:**
> After installing Fedora, I ONLY can boot to Fedora. Any suggestions?
Thanks, again.

I've never used Fedora, but it probably installed Grub (overwriting the Grub Ubuntu installed). Just edit the /boot/grub/menu.lst file in Fedora and add a new entry for Ubuntu.

(I can't give you excact entry as I don't know your parttion layout, and I don't have any Linux machine available now, but you could just mount the Ubuntu partition and check the correct entry from ubuntu's menu.lst file)

---

