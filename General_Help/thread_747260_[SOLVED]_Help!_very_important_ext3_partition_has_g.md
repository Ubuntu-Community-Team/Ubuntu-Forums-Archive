---
title: "[SOLVED] Help! very important ext3 partition has gone totaly fubar!"
date: 2008-04-06
forum: General Help
---

### Post by marshall.robert on 2008-04-06
The partition in question (/dev/sda4) holds all my work, my source code, business files emails and firefox data. It is formatted using the ext3 file system, and is shared between Linux and XP this has worked fine for a good period of time, but I recently installed osx86 on this machine because its the only one that can handle it, but I foolishly didn't back up my important data.

During the install I told osx to use a set partition I had set aside for it thinking that all would be good I went ahead, and then I went with my reinstall of windows (it kept bsoding) and when installed the driver and setup the disc windows asked me to format it, I said no and wondered what could be wrong.. 

During the driver setup it recognised the partition as a linux file system, but after i reinstalled grub I promptly booted ubuntu and I was asked for the root password during boot up, so I gave it and logged in, it told me that e2fsck couldn't find /dev/sda4 - e2fsck: No such file or directory while trying to open /dev/sda4 - and then told me to do e2fsck -b 8193, so I did and it spat out the same error. I then logged out and proceeded with the boot, and it told me it couldn't find /dev/sda4 to mount.

After I logged in tried to do e2fsck -b 8193 again, again it didn't work so I tried e2fsck -b 8194, still didn't work. I then proceeded to open gparted and it tells me that the space is unallocated....

I then had a little bit of a panic and came here to see if anyone here can sort out my (pretty dire) problem..

I don't understand how my most important partition gets wrecked and yet the others are left unharmed....

Please say if any of this makes no sense.

Please help?

Thanks in advance.

-rob

---

### Post by marshall.robert on 2008-04-06
I just booted into a live cd and did e2fsck /dev/sda and it gave me this:
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


then fsck /dev/sda:
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

anyone have any ideas? please?

---

### Post by mick8985 on 2008-04-06
I have heard that sometimes if you recover the partition table you can mount the partition, however in this case it seems that the partition table is completely intact but the filesystem has been corrupted. There is proprietary software you can use to recover the data 
[http://www.datarecoverylinux.com/]("http://www.datarecoverylinux.com/")
$49 seems quite reasonable, unfortunately I am not aware of any free software alternatives. The other alternative is to pay a data recovery company to do this for you, which is very pricey. Taking into account the value of the data you have lost I'd just pay for the software.
At least in future you'll be sure to never make the mistake of not backing up important documents ;)

---

### Post by marshall.robert on 2008-04-07
Thanks for the link, i downloaded the demo, but it only found my Ubuntu partition, which proves it can find them, but it cant help.

I think the partition has been deleted, but im thinking (hoping) that a delete only makes it deleted in the partition table and not actually deleted....

---

### Post by mick8985 on 2008-04-07
In that case if you haven't resized any of the partitions it should be a matter of using fdisk to recreate the partition and run fsck on the partition. if that works just mount it.

---

### Post by marshall.robert on 2008-04-07
im sorry i was wrong, it has now just fiound it!!!!!!

after i get the data (given it works) i will try that method you suggest

---

### Post by mick8985 on 2008-04-07
Well keep me posted, I'd be interested to know if it works

---

### Post by marshall.robert on 2008-04-07
Well since it doesnt actually let you save the data, cos its a trial, ive looked for other methods. i have actually found a linux app (trial again) [http://www.downloadjunction.com/product/store/32237/index.html](http://www.downloadjunction.com/product/store/32237/index.html) and im seeing how that works out.

im not very confident about myself using anything like fdisk cos im not that experienced with it, but if all else fails ill give it a shot.

---

### Post by marshall.robert on 2008-04-07
Well i got the data back which is a relief

a friend lent me a thing called Acronis which appears to be a linux live cd made to look exactly like XP and is made for this kind of problem and it worked through vmware too...

How do you mark as solved?

---

### Post by mick8985 on 2008-04-08
Glad to hear it, at the top of the thread there is a menu called thread tools

---

### Post by marshall.robert on 2008-04-08
ahh yes, thanks, and its a shame i couldnt do your method, would have been good to try. thanks for your support.

---

