---
title: "Swap Partition"
date: 2007-05-31
forum: General Help
---

### Post by Gagle on 2007-05-31
To make a long story short,  I need to manually remount my swap partition on my older laptop running Edgy.

I think I edited my /etc/fstab file appropriately, changing the file system. (i.e : changed /dev/hda5 to /dev/hda2) 
Before, the Swap partition was a logical partition in an Extended partition (In fact, the swap partition took the whole  Extended partition place) and now is a Primary partition.  
I did not take this consideration in the fstab file, not knowing how to edit the changes appropriately.  

This being said,  I don't know how to check for available mounted partitions etc..  

Any help would be appreciated.  

Gagle

---

### Post by merlinus on 2007-05-31
IN a terminal:

```

sudo fdisk -l
blkid

```

the l is a lowercase L.

The first will give your partitions, and the second the UUIDs for each.

Compare that with your /etc/fstab

Good luck!

-merlin

---

### Post by Gagle on 2007-05-31
Great !!

Thx a ton. 

regards,

Gagle

---

### Post by trak87 on 2007-05-31
> check for available mounted partition

In addition to the other suggestions (I didn't know about blkid), I might use the following:

```
df -h
```

```
clear; sort /etc/mtab
```

/etc/fstab shows what's mountable, but I think /etc/mtab shows what's actually mounted. Somebody correct me if I'm wrong.

---

### Post by trak87 on 2007-05-31
Gee whiz. Neither df -h nor /etc/mtab show the swap drive at all...

Seems "sudo fdisk -l" is the way to go.

---

### Post by Gagle on 2007-05-31
The blkid command outputs the mounted partitions in this fashion : 

~$ blkid

/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="fc316e1e-ec09-423f-9181-8ce6a2da0b93" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="90960b72-f361-4121-85b1-47108d73e291" TYPE="swap" 

Please note that this is not the situation of the laptop.  Just an example from a working computer with an internet connection.....

Here is the potential error : 

When I execute the blkid command on my laptop, the swap partition appears without any UUID 
but the other partitions are attributed UUID.

In fact, the swap is listed as follows : /dev/hda2  TYPE="swap"

My question :  Is it necessaery to have a UUID associated with this partition ?

---

### Post by Gagle on 2007-05-31
The " free " command should do the trick :P

Here is its output :
```


~$ free
                total       used       free     shared    buffers     cached
Mem:       109780    107160     2620          0      1308   23104
-/+ buffers/cache:     82748     27032
Swap:       0          0     0



```

So the swap seems mounted, but not working.

Any sugestions ?

Gagle

---

### Post by trak87 on 2007-05-31
Editing /etc/fstab should do the trick. Did you reboot?

---

### Post by Gagle on 2007-05-31
> **trak87 said:**
> Editing /etc/fstab should do the trick. Did you reboot?

I did reboot and editing the fstab file seems to be the issue at hand.
The UUID is waht I think is causing such havoc.

FYI, the reason I am in such trouble is that I re-partitionned my hard drive to install VectorLinux from a Direct Linux Host.  Given the fact that you can  only have ONE Extended partition (and as told before, the swap was taking that spot) I had to redo my partition table.

Now, I know the Swap is fuubar because the installation lags and kills processes in order to free memory.

I love computers :guitar:

Gagle

---

### Post by trak87 on 2007-05-31
Using /dev/<drive> should work in addition to the global id number.

Check out this page. It seems to cover everything discussed in this thread so far, but it might help:

[http://hype-free.blogspot.com/2007/04/moving-to-ubuntu-swap-partition.html](http://hype-free.blogspot.com/2007/04/moving-to-ubuntu-swap-partition.html)

---

### Post by trak87 on 2007-05-31
The problem seems to be the ever changing nature of Linux. What worked before doesn't work now... Try this page. Guy had a similar problem  and seems to have solved it:

[http://www.linuxquestions.org/questions/showthread.php?t=554639](http://www.linuxquestions.org/questions/showthread.php?t=554639)

---

### Post by Gagle on 2007-05-31
Everything Worked out great !

Thanks a lot to all of you for your support.

regards,

Gagle

---

