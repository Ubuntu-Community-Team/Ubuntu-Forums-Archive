---
title: "[SOLVED] Porting an entire installation"
date: 2008-05-20
forum: General Help
---

### Post by bilijoe on 2008-05-20
I have been living with an old 40Gb HDD, but recently acquired an shiny new Segate 250Gb drive.  Obviously, I want to replace the old 40Gb with the new 250Gb, but I don't want to have to go through the whole process of installing the OS, installing all the additional stuff, setting up all my preferences, etc.  A while back, I did a similar thing, where I .tar'ed my current system from one drive (that time, I was going from 18GBb to the now current 40), and un.tar'ed (de.tar'ed?) the whole mess to the new drive.  When I did that, the system would no longer boot.:(  It would get part way into the boot process, but not far enough to bring up the recovery console.  With some very helpful hand-holding by tamoneya (thanks again tamoneya:)), I managed to get things working again.  I'd like to avoid all the hubbub this time, if I can.  Can anyone tell me the "correct" way to transfer a working installation to a different HDD, with the least amount of headache?  I'd be greatly appreciative.:popcorn:

---

### Post by HermanAB on 2008-05-21
dd

---

### Post by ryanhaigh on 2008-05-21
What you want to do is create an image of your drive, you can indeed do this with dd but there may be easier alternatives such as partimage [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page). Because its in the repositories you can boot the livecd, install partimage and use it from there. There are others also such as ghost for linux, clonezilla and commercial apps such as acronis trueimage.

That said I would recommend keeping the 40gb drive and using that for your oses and use the 250 for your personal data (/home).

---

### Post by bilijoe on 2008-05-21
> **HermanAB said:**
> dd dd?:confused:  Excuse me, but I must have missed something.

---

### Post by bilijoe on 2008-05-21
> **ryanhaigh said:**
> What you want to do is create an image of your drive, you can indeed do this with dd but there may be easier alternatives such as partimage [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page). Because its in the repositories you can boot the livecd, install partimage and use it from there. There are others also such as ghost for linux, clonezilla and commercial apps such as acronis trueimage.

That said I would recommend keeping the 40gb drive and using that for your oses and use the 250 for your personal data (/home). I had wondered if that mightn't be a good idea, and it certainly would eliminate any concerns about moving the system (not to mention, save a lot of time).  The new drive is much faster though (that is, if specifications mean anything).  Do you think I'd be giving up any significant amount of performance by leaving Linux on the 40?  Also, to make the 250 "/home", is it as simple as just putting into its properties that its mount point is /home, or is there more to it than that?

---

### Post by ryanhaigh on 2008-05-21
dd is an application that you CAN use to do what you want but there are other projects such as those I mentioned that will make it easier.

I can't really say whether you will get any percievable performance benefit from using the newer drive, I dont often do anything io heavy and the linux cache mechanism (and stability) keeps things i access in memory.

It is a little complicated to move your /home but as with most things you can get help here. Here is a howto I found [http://ubuntuforums.org/showthread.php?t=250104](http://ubuntuforums.org/showthread.php?t=250104), don't have time to read through it right now but if something is unclear just post back and Ill help you out.

---

### Post by bingoUV on 2008-05-21
First, I would say faster hard disk matters a lot in performance. Disk being the slowest device, any improvement in disk speed is sure to improve the overall performance.

Do you have many partitions in the 40GB hard disk? Would you like to have similar number of partitions after the transition, or one of the following would suit you?
1. One or more partitions in the ~210 GB extra space.
2. Last partition inflated to fill the extra space.

These two options are simple. First a dd, and some gparted magic from live cd. 

If you want all partitions larger, individual partition dd and e2resize should solve the problem. Depends on how you want to configure your new hard disk.

---

### Post by ryanhaigh on 2008-05-21
After the resize however you will also need to adjust the entry for the partition in /etc/fstab as the UUID of the partition will have changed.

---

### Post by bingoUV on 2008-05-21
> **ryanhaigh said:**
> After the resize however you will also need to adjust the entry for the partition in /etc/fstab as the UUID of the partition will have changed.

yes, I had forgotten that. grub's menu.lst and /etc/fstab might also need updating if these use UUID.

---

### Post by Ramses de Norre on 2008-05-21
I've done this with a simple cp -a and everything worked perfectly. Be sure to do it when you're not running from the partition being transferred though.

---

### Post by unkilbeeg on 2008-05-21
You may also want to try the [Clonezilla]("http://www.clonezilla.org") LiveCD.  It uses dd or partimage, or several other programs depending on the nature of what you're copying.  You define the order it tries to use them, and it picks the one that works the best.

It's certainly able to copy from one physical disk to another.  I've also found it useful for propagating an image from one machine to another -- if you can get that base image small enough, Clonezilla has utilities that allow you to create a LiveDVD that contains your image and automatically installs it.

---

### Post by bilijoe on 2008-05-22
> **Ramses de Norre said:**
> I've done this with a simple cp -a and everything worked perfectly. Be sure to do it when you're not running from the partition being transferred though. According to man,  "cp -a" is equivalent to "cp -dpR".  After reeding what the options -d, -p, and -R do, it occurs to me it might be better (i.e., safer, or more accurate)  to use ```
cp --preserve=all -R
```Any comments?

---

### Post by ryanhaigh on 2008-05-22
The copy everything method used to work very well and was obviosuly the simplest way to clone and install (although I put it in a tar archive for convinience), however because ubuntu moved to uuids things have gotten a little more complex and using this method requires more work than the simple cloning because the uuid is not preserved. 

Another thing which I forgot to mention is your ethernet devices may be named differently, eth0 etc. are bound to specific mac addresses and so on the new install the first ethernet device may be eth1 instead. The persitant names/binding uses information in the /etc/iftab file and so deleting the entry from there should get your ethernet devices named 'properly' again. Note that this is applicable to all methods.

---

### Post by bilijoe on 2008-05-22
> **ryanhaigh said:**
> The copy everything method used to work very well and was obviosuly the simplest way to clone and install (although I put it in a tar archive for convinience), however because ubuntu moved to uuids things have gotten a little more complex and using this method requires more work than the simple cloning because the uuid is not preserved. 

Another thing which I forgot to mention is your ethernet devices may be named differently, eth0 etc. are bound to specific mac addresses and so on the new install the first ethernet device may be eth1 instead. The persitant names/binding uses information in the /etc/iftab file and so deleting the entry from there should get your ethernet devices named 'properly' again. Note that this is applicable to all methods. Will that method, deleting the UUID entries from menu.lst, and /etc/fstab, automatically correct those too?  Or do you have to edit those manually?

---

### Post by ryanhaigh on 2008-05-22
You will have to manually replace the UUIDs that are currently in fstab and grub (and somewhere else to do with suspend/resume) with the ones for the new partitions.

---

### Post by Ramses de Norre on 2008-05-27
Or even better, label your partitions and get rid of those UUIDs, more info can be found [here](http://wiki.archlinux.org/index.php/Persistent_block_device_naming#by-label).

---

