---
title: "Check my fstab please!"
date: 2007-01-12
forum: General Help
---

### Post by btboudreaux on 2007-01-12
Hi, I was wondering if someone could check my fstab entry and tell me if anything is wrong with it, and I have some questions. I have a couple drives configured like this....

```
UUID=XXXXXXXXXXXXXXXXXXXXXXXXXXX  /media/05-Backup   ext3         
sync,errors=remount-ro,user,dirsync  0  1
```

First off, I wanted to make sure that if power was lost, I wouldn't have any data loss. Is this a correct configuration for that scenario? I have sync so that things are directly written to the drive, but do I need dirsync? What exactly does dirsync do? My write times seem to be very slow, I was wondering if dirsync had a big performance impact.

Anyhow, any advice would be appreciated. Thanks!

---

### Post by taurus on 2007-01-12
I am not sure why and how you get this in your /etc/fstab because it's not even closed!  You need to change it to whatever actual partition is, something like /dev/hdb1.

```
UUID=XXXXXXXXXXXXXXXXXXXXXXXXXXX
```

---

### Post by brt on 2007-01-12
> **taurus said:**
> I am not sure why and how you get this in your /etc/fstab because it's not even closed!  You need to change it to whatever actual partition is, something like /dev/hdb1.

```
UUID=XXXXXXXXXXXXXXXXXXXXXXXXXXX
```

hmm, this is what you get on any default install since fiesty.  it uses UUID per default instead of devicenames, i think it also happens if you upgrade to fiesty.


there is an interesting thread regarding fstab:

[http://www.ubuntuforums.org/showthread.php?&t=283131]("http://www.ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Jongi on 2007-01-12
Hmmm, fstab by UUID. Not sure that is easier than by device name. 

I've been using Linux for the last 3 years but have never known how to get the UUID for any of my devices. I suspect it's pretty easy to get it, but is it easy to remember?

---

### Post by bodhi.zazen on 2007-01-12
You can list your devices by uuid with:```
ls /dev/disk/by-uuid -l
```

I know feisty uses UUID =XXXX by default, I thought edgy did too ... ??

You can use 

/dev/hdxy

in Feisty in place of UUID=XXXX

I think the question is in regards to the options.

I do think the file system should be mounted sync

---

### Post by Jongi on 2007-01-12
I have no fundamental issue against mounting by UUID. My issue is making it the default (without there being a concerted effort amongst other distros - or am I wrong about this?)

I just feel that it could be the kind of thing that stops people from using Ubuntu or its variants. I personally am a multi-booter, so if Ubuntu and variants pose an extra challenge, I might easily not use it.

Obviously not all users are like me and the ubuntu powers that be have thought about this. I suspect this is the way distros will go but ubuntu might be ahead of themselves by making it the default.

---

### Post by brt on 2007-01-12
i think the reason why it has been decided to use UUID is that with UUID's fstab/mounting does not depend on device names anymore. especially with sata und usb drives the device name can change, e. g. if you change the order of the devices when plugged in. sda can easyly become sdb or sdc or whatever depending which device you plug in first.

UUID makes it possible to use the correct partition without taking care of the device names :)

---

### Post by glabouni on 2007-01-12
I've been wondering what those UUID were and why did they replace the usual /dev/hda1 and such. It is default in edgy, and should not to be of any trouble as right before teach UUID line in fstab you find a commented /dev/hda equivalent.

Another thing I'm wondering about is, how come no one has even tried to answer the question that was asked here ?

> **Jongi said:**
> Hmmm, fstab by UUID. Not sure that is easier than by device name. 

I've been using Linux for the last 3 years but have never known how to get the UUID for any of my devices. I suspect it's pretty easy to get it, but is it easy to remember?

```
blkid
```

---

### Post by btboudreaux on 2007-01-12
UUID has been asked and answered on many threads.

Can someone please respond to the original subject matter.

---

### Post by brt on 2007-01-12
> **bodhi.zazen said:**
> I know feisty uses UUID =XXXX by default, I thought edgy did too ... ??

sure you are right, its default since edgy !

---

### Post by ~LoKe on 2007-01-12
Yep, UUIDS are fine.

And you shouldn't have dataloss so long as you're using the right filesystem (ext3) without journaling.

---

### Post by glabouni on 2007-01-12
I didn't even know about dirsync option 3 minutes ago. 
```
man stab
man mount
/dirsync
```

and now I can tell you what is afected by dirsync:
> dirsync                     
All directory updates within the file system should be done synchronously.  This affects the follow&#8208;ing system calls: creat, link, unlink, symlink, mkdir, rmdir, mknod and rename.

this was a kind way to say RTFM! I guess.

now, you should now that using sync instead of async impacts performances. And moreover that there is absolutely no way to be absolutely certain you won't lose any data in case of power cut. But you can dramatically reduce the odds, using ext3 as your fs is a start and coupling your computer to a UPS would definitely help.

---

### Post by btboudreaux on 2007-01-12
> **glabouni said:**
> I didn't even know about dirsync option 3 minutes ago. 
```
man stab
man mount
/dirsync
```

and now I can tell you what is afected by dirsync:


this was a kind way to say RTFM! I guess.

now, you should now that using sync instead of async impacts performances. And moreover that there is absolutely no way to be absolutely certain you won't lose any data in case of power cut. But you can dramatically reduce the odds, using ext3 as your fs is a start and coupling your computer to a UPS would definitely help.

I've man fstab, and man dirsync with no results. Didn't man mount, and ive searched google and the forums. So I did RTFM, just not in the right place. Thanks for answering though.

---

### Post by glabouni on 2007-01-13
Happy to be of any help. Missing some important infos while RingTFM happens to me more often than I'd like. I guess when you did man fstab, you missed this:

> The fourth field, (fs_mntops), describes the mount options associated with the filesystem.

       It is formatted as a comma separated list of options.  It contains at least the type of mount plus any  additional options  appropriate to the filesystem type.  **For documentation on the available options for non-nfs file systems, see mount(8). ** For documentation on all nfs-specific options have a look at nfs(5).  Common for all types of  file system  are  the options &#8216;&#8216;noauto&#8217;&#8217; (do not mount when "mount -a" is given, e.g., at boot time), &#8216;&#8216;user&#8217;&#8217; (allow a user to mount), and &#8216;&#8216;owner&#8217;&#8217; (allow device owner to mount), and &#8216;&#8216;comment&#8217;&#8217; (e.g., for use  by  fstab-maintaining programs).  The &#8216;&#8216;owner&#8217;&#8217; and &#8216;&#8216;comment&#8217;&#8217; options are Linux-specific.  **For more details, see mount(8)**.

---

### Post by btboudreaux on 2007-01-13
> **glabouni said:**
> Happy to be of any help. Missing some important infos while RingTFM happens to me more often than I'd like. I guess when you did man fstab, you missed this:

touché

---

