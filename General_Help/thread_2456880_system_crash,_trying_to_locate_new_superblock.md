---
title: "system crash, trying to locate new superblock"
date: 2021-01-21
forum: General Help
---

### Post by Drenriza on 2021-01-21
Hi all
Yesterday i had a system crash and today my laptop boots into busybox (initramfs).

I am running ubuntu 20.04 with LUKS for full disk encryption.

I have tried to run fsck.ext4 /dev/mapper/system-root but i am getting a dm-1 error on block 118518768
**_try and run e2fsck -b block device_**

I dont know what block size Ubuntu is installed with, to try and locate a new superblock i can boot from.
Is there a way from busybox that i can list all possible superblocks if i know the block size?

I rarely ever deal with fsck so my experience with it is extremely limited.

When i type exit in busybox i get the error

> 
buffer i/o error on dev dm-1 logical block 110518768 async page read
fsck.ext4 input/output error while trying to open /dev/mapper/system-root
The superblock could not be read or does not describe a valid ext2/3/4 filesystem


Any and all suggestions are most welcome!

Best regards!

---

### Post by ActionParsnip on 2021-01-21
Try:
```

e2fsck -b 32768 /dev/whatever 

```

The superblock is very important and there are multiple copies across the drive

---

### Post by Drenriza on 2021-01-21
Hi ActionParsnip

Doing so gives the error

> 
e2fsck 1.45.5
buffer_io_error: 4 callbacks suppressed
Buffer I/O error on dev dm-1, logical block 2048, async page read
Buffer I/O error on dev dm-1, logical block 4096, async page read
Buffer I/O error on dev dm-1, logical block 8193, async page read
Buffer I/O error on dev dm-1, logical block 16386, async page read
Buffer I/O error on dev dm-1, logical block 32772, async page read
e2fsck: input/output error while trying to open /dev/dm-1

The superblock could not be read or does not describe a valid ext2/3/4
(initramfs) _


---

### Post by Drenriza on 2021-01-22
Hi all
Anyone who can advice on how i can resolve my above problem?

Thanks in advance
Best regards!

---

### Post by ActionParsnip on 2021-01-22
Did you search the web for the error you see?

---

### Post by dinkidonk on 2021-01-22
Does the device unlock correctly? If not, do you by change have a backup of the LUKS header? Is it a SSD or a HDD?

[This might be helpful](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/).

---

### Post by Drenriza on 2021-01-26
> Did you search the web for the error you see?
Yes and so far i have not been able to resolve it.

> Does the device unlock correctly?
I believe it unlocks correctly, but how can i verify this?

> do you by change have a backup of the LUKS header?
I do not

> Is it a SSD or a HDD?
It is a SSD

Thanks for the guide!
I tried it out, but in initramfs i dont have access to 
sudo mke2fs -n /dev/xxx

to see my superblock locations and all the blocks i have tried to far gives me the message of that its not a valid superblock.

---

### Post by dinkidonk on 2021-01-26
SSD's are notoriously known for corrupting if exposed to sudden power loss before the write cache is properly flushed, so that's bad news. If possible, I would try to access the drive from another system running Ubuntu/Linux (eg. a bootable USB stick) - I do not think you will be able to get any further from within a broken system.

---

### Post by Drenriza on 2021-01-26
> **dinkidonk said:**
> SSD's are notoriously known for corrupting if exposed to sudden power loss before the write cache is properly flushed, so that's bad news. If possible, I would try to access the drive from another system running Ubuntu/Linux (eg. a bootable USB stick) - I do not think you will be able to get any further from within a broken system.


I tried to live USB into ubuntu 20.04, was able to decrypt the disk and load the LVM volume.
Ran a fsck on the LVM group and fsck came back with

"still contains errors"

after it was done. Tried to run fsck a second time, but than i got prompted again with bad superblock immediately.

---

### Post by dinkidonk on 2021-01-26
Did you try the guide from #6 while booted into the live USB?

---

### Post by Drenriza on 2021-01-26
> **dinkidonk said:**
> Did you try the guide from #6 while booted into the live USB?

yes, that is what i did in #9

But since i use en encrypted disk i used parts from two guides

[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
[https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/](https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/)[URL="https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/"]
[/URL]
And read comments from 
[https://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](https://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)
.

---

### Post by Drenriza on 2021-01-26
So it seems that all my stored superblocks are not functional, and i have found a program called testdisk that might be able to do something.
But i cannot find the package on ubuntu live usb 20.10

apt-get update
apt-get install testdisk

anyone knows why?

---

### Post by tea for one on 2021-01-26
> **Drenriza said:**
> So it seems that all my stored superblocks are not functional, and i have found a program called testdisk that might be able to do something.
But i cannot find the package on ubuntu live usb 20.10

apt-get update
apt-get install testdisk

anyone knows why?

You may have to enable other repositories in a live session:-
```
sudo add-apt-repository universe

``````
sudo add-apt-repository multiiverse

``````
sudo apt update
```

---

### Post by Drenriza on 2021-01-26
Thanks for the reply tea for one!

Does anyone know of a way i can mount my drive, with no superblocks working so i can extract data i would like to recover?
I have tried to mount the drive with

sudo mount /dev/system/root /media/mounttmp

but mount comes and say that no working superblocks can be found after working for quite a while and errors out.
Can it be mounted in a special way where superblocks arent a issue?

---

### Post by dinkidonk on 2021-01-26
Superblocks contain vital information about the file system and without any valid superblocks the file system is de facto broken and thus cannot be mounted. TestDisk works on unmounted volumes, you should run TestDisk on the unlocked volume / mapper (eg. /dev/dm-X). TestDisk may be able to fix the file system and if not, PhotoRec (part of testdisk) may be able to recover some of the files - but read the docs carefully before starting!

---

### Post by Drenriza on 2021-01-27
Thanks for the help all.
testdisk was not able to fix any of the superblocks or partition tables, so i used testdisk to extract the files i wanted to recover and will reinstall my OS on a new SSD.
Are there any types of SSD's you can recommend that better can handle untimely shutdowns or system crash so i can avoid such a problem in the future?

---

### Post by dinkidonk on 2021-01-27
Great that you got your files recovered. No SSD can securely handle a power loss but stay away from the cheapest ones, personally I have good experiences with Crucial's MX series.

---

