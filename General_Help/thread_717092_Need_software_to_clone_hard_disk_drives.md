---
title: "Need software to clone hard disk drives"
date: 2008-03-06
forum: General Help
---

### Post by MountainX on 2008-03-06
**UPDATE**
This thread is partially solved. Before I mark it [SOLVED]** I would like to know if anyone has any ideas about an alternative to 'dd' when the target drive is larger than the source.** Will 'dd' really not work if the target is larger?

Clonezilla would not clone my drives because they don't have a partition table, etc. (They are out of a RAID array.) 
-----------------

Hi,
I have a 300GB SATA HDD with data and another empty 300GB HDD. I want to clone the first drive onto the second. I want a low level clone -- an exact image of the drive. What software should I use?

I plan to plug the 2 HDDs into my motherboard. I have 1 Sata drive installed now and I use that one to boot Ubuntu. When I plug the 2 additional drives in, I do not want Ubuntu to write anything to either disk (other than when I do the cloning procedure).

Tips are appreciated. (BTW, I already read the following thread and didn't find my answer: [http://ubuntuforums.org/showthread.php?t=500621](http://ubuntuforums.org/showthread.php?t=500621)).

Thanks.

P.S. The drive I will be cloning doesn't have Linux partitions on it. It is one drive out of a 4-drive RAID array. Actually, I'm going to clone all 4 of the RAID drives this way because my next step is to change some settings on the RAID controller. If I screw up, I want to have 4 drives that are exact images of the 4 drives currently in the RAID array.

---

### Post by jonnymccullagh on 2008-03-06
Have you checked CloneZilla Live CD ?

---

### Post by PeterJS on 2008-03-06
If both drives are offline (ie not mounted) and exactly the same size. You could use:
```

dd if=/dev/source of=/dev/destination

```
And that will copy the source to the destination byte for byte including empty space. But it's important that the neither drive is written to by an outside source as that will screw up your imagine, and also that they are the same size, as it's doing a byte level copy so it's expecting a disk with the same size and layout for the destination.

---

### Post by MountainX on 2008-03-06
I am looking at Clonezilla. I see the docs say, "However, clonezilla, containing some other programs, can save and restore not only partitions, but also a whole disk."

However, I was hoping for an application I could run rather than making and booting from a CD. Obviously, that's a minor issue however. 

I do like the idea of using 
```
dd if=/dev/source of=/dev/destination
```

That will work for 2 of my 4 drives. However, the other 2 are 320GB drives that were truncated to 300GB by the RAID controller... so that sounds like I will have a problem. I do have two 500GB drives I can use as the destinations, but apparently that won't work for dd.

I'm still looking for more options or more feedback. Thanks.

---

### Post by MountainX on 2008-03-06
> **PeterJS said:**
> If both drives are offline (ie not mounted) and exactly the same size. You could use:
```

dd if=/dev/source of=/dev/destination

```


I ordered two 320GB drives, so now I will be able to clone each original drive onto a new drive that is the exact same model.

To use dd as shown above, how will I know which drive is the source and which is the destination? Are the device names guaranteed to correspond with the motherboard's SATA channel numbering?

I assume I'll be safe if I don't take action to mount these drives. They won't be mounted automatically will they?

I know this is probably a dumb question, but is it possible to "hot plug" a SATA HDD while the computer is running? I have the SATA cable and the power cable in place, so I could just plug the drive in. Obviously, the motherboard isn't designed to hot swap hard drives, but since they aren't mounted, would this work? 8-[

Thanks again

---

### Post by PeterJS on 2008-03-06
> **MountainX said:**
> I ordered two 320GB drives, so now I will be able to clone each original drive onto a new drive that is the exact same model.

To use dd as shown above, how will I know which drive is the source and which is the destination? Are the device names guaranteed to correspond with the motherboard's SATA channel numbering?

I assume I'll be safe if I don't take action to mount these drives. They won't be mounted automatically will they?

I know this is probably a dumb question, but is it possible to "hot plug" a SATA HDD while the computer is running? I have the SATA cable and the power cable in place, so I could just plug the drive in. Obviously, the motherboard isn't designed to hot swap hard drives, but since they aren't mounted, would this work? 8-[

Thanks again

Don't know about the SATA hot plug, if the motherboard isn't designed to support it it's probably best not try.

I assume (or rather hope, because it makes life easier) that the source drives are in use and being mounted some where in your existing file system and you'll have to manually unmount them before cloning them. If they are mounted you can run mount with no parameters and it will output what devices are mounted where. It's probably safe to assume that they will be mounted in the ordering of the SATA channels, but it certainly wouldn't hurt to test that by mounting them and inspecting their contents.

As for automounting, if the drives are formatted I believe they will be automatically mounted in /media/, but if they are unformatted they can't be mounted. Again better safe than sorry. My use has always been from a liveCD backing up my root file system to a USB drive, just as a point of reference.

---

### Post by MountainX on 2008-03-06
Currently the drives are not mounted anywhere. They are out of a Windows 2003 server with an Areca RAID controller.

I have the 4 existing drives sitting on my desk (not plugged in to anything). Soon I will have 4 idential new drives that I'll use to clone these. It would be great if I can just clone them using 'dd' without having to download an image, burn a CD and boot from the CD.

After I clone them, I'm going to put them back in the server.

(OT, but one reason I don't want to try the live CD is that my computer would not boot from the Ubuntu Live CD when I originally tried to install Ubuntu. In fact, I tried the Ubuntu Live CD on 3 different computers and it wouldn't boot on any of them -- and the CD itself was good. I think the problem was the video cards. One was too old and the other two are listed in my signature.)

P.S. The whole story of why I want to clone these 4 drives is here: [http://www.hardforum.com/showthread.php?t=1280327](http://www.hardforum.com/showthread.php?t=1280327)

---

### Post by MountainX on 2008-03-06
**[SIZE="4"]I need help using Clonezilla please.[/SIZE]**

I downloaded it and I can boot up with it just fine. Doing a local_disk to local_disk clone, I get to a menu that asks me to choose the local disk as source. The choices are:
sda Maxtor_7L300S0__
sdb Maxtor_7L300S0__

As far as I can tell, there is no way to tell which disk is which. When I plug them in one at a time, no matter which SATA port I use on the motherboard, the one disk is always sba. Since the device name is not tied to the SATA port,  I assume either disk could be sdb when I plug the second one in.

These disks don't have a linux file system, so I can't mount them. They don't even have a FAT or NTFS file system because they came out of a RAID controller. 

How can I find out which disk is which? :confused:

---

### Post by Taino on 2008-03-06
np :)

---

### Post by MountainX on 2008-03-06
I appreciate the reply, but that doesn't answer my question. I have two disks on two different SATA channels. If I unplug either one and don't change anything about the other one, the remaining disk is always sda. Do you see what I'm saying?

---

### Post by bodhi.zazen on 2008-03-06
You can identify the disk by uuid or setting a label.

To show the disk by uuid, plug them in and run :

```
sudo blkid
```

You can then add an entry in fstab to mount them by uuid.

You can also set a label. 

See this link for additional information :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by MountainX on 2008-03-07
blkid doesn't find the disks. Does blkid only find mounted disks?

I can't (and don't want to) mount the disks. I am cloning disks from a RAID array -- they don't have any file system on them. I just want to clone disk to disk.

I assume since I am not mounting or formatting them, I can't label them. That's why I need to identify them by serial number.

Clonezilla live cd doesn't have hdparm or sdparm (at least not that I can find). But it does have udevinfo. I ran this command:

```
udevinfo -a -p $(udevinfo -q path -n /dev/sdd)
```

Unfortunately, even that doesn't list the serial number or anything else I could find that would differentiate two drives with the same model number and firmware.

What are my other options? Thanks for the help.

---

### Post by MountainX on 2008-03-07
OK, I found the solution to getting a HDD serial number so I can tell which drive is sda and which is sdb.

```
udevinfo --query=all --path mypath
```

That gives me the serial number of the disks. Now I can run Clonezilla (or dd, etc.)

Thanks to bodhi.zazen for the link that led me to the solution.

---

### Post by MountainX on 2008-03-07
I'm going through the Clonezilla menus and at the "advanced extra parameters" I'm not sure what to use. The default is "reinstall grub". Since this isn't a bootable disk I'm cloning, I don't want that.

1. reinstall grub in target
2. resize to fit
3. do NOT show GUI of partimage
4. do NOT create partition table
5. do NOT clone boot loader
6. force to load saved HD CHS value
7. batch mode
8. verbose

I think options 4 & 5 would apply, but I'm not sure. Any suggestions? Thanks.

Should I just go back to trying dd?

---

### Post by tgalati4 on 2008-03-07
Sounds like this is more difficult than it needs to be.

Boot the Live CD, go to a terminal:

>sudo cp /dev/sda /dev/sdb

(Wait . . . .)

Swap drives and boot to verify that you have a clean copy.

---

### Post by MountainX on 2008-03-07
Clonezilla isn't cloning.... I've tried several different options with no luck and various errors messages -- or no error but no clone.

However, since I booted up with the Clonezilla, I just went into the shell and typed:

```
 sudo dd if=/dev/sda of=/dev/sdb 
```

And now I can hear the drives being cloned... it seems to be working.

---

### Post by MountainX on 2008-03-07
Should I have used the notrunc option?

```
dd if=/dev/sda of=/dev/sdb conv=notrunc,noerror
```

I came across the above command at this link:
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Also, I now see that dd gives no progress status or other output unless one is advanced enough to know how to send a USR1 signal to the running 'dd' process. Since I didn't send dd to the background when I started it, I guess I'm stuck with no progress info now... read the help more carefully than I did if you are new to dd.

---

### Post by Carl H on 2008-03-07
> **MountainX said:**
> I know this is probably a dumb question, but is it possible to "hot plug" a SATA HDD while the computer is running?

I very strongly recommend that you do not do this.

---

### Post by MountainX on 2008-03-07
The first drive finished cloning while I slept. 'dd' reports this:
586114704+0 records in
586114704+0 records out
300090728448 bytes (300GB) copied, 14601.6 seconds, 20.6 MB/s

**doesn't that seem really slow?**

Anyway, I like the 'dd' command for this kind of disk cloning. **Thanks for the help** with that.

I don't think Clonezilla will work when the disk doesn't have a partition table or file system (which mine don't because they are members of a raidset).

I would be curious what tools would work if my target drive was larger. I would like to clone my two 320 GB drives today and (until next week) I only have two 500 GB targets.

---

### Post by MountainX on 2008-03-08
bump

Clonezilla didn't work.

'dd' did work when the target drive was the same size as the source. It also worked without the notrunc option (although I'll use that next time).

**What tools would work if my target drive is larger?**

Thanks

---

