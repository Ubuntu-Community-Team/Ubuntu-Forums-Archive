---
title: "[SOLVED] GParted LiveCD drive resizing gone wrong"
date: 2008-04-02
forum: General Help
---

### Post by 4Foot on 2008-04-02
I have a 70 Gig drive with Hardy on it and it was partitioned as follows.

root 13 Gigs Sda1

Data 54 Gigs Sda6

Swap 3 Gigs 

I had permissions problems with Sda6 and could not get that fixed but I needed to make root larger because, for instance, a prog like DeVeDe would not write to Sda6 and would tell me that I did not have enough room to create a DVD file set on Sda1.

After some thought, I got my hands on Gparted LiveCD, booted into it and attempted to 'grow' Sda1 by 10 gigs. No joy.

I then decided that I needed to create room for it to 'grow" so I 'shrunk' Sda6 by 10 gigs successfully. I was very pleased with myself.

However, I now have an 'unallocated' drive of approx. 10 gigs and when I try to 'grow' Sda1 into that space it just does not allow me to do anything with it unless I want to shrink it.

Thinking it was unavailable, I chose the unallocated drive, clikked on 'new' and created it as an ext3 drive. Then I retried 'growing' Sda1 into that space and still no joy.

So, I have made available 10 gigs of space but cannot get my Sda1 to use it. I would be grateful for some insight into the reasons for my failure in this matter. 

Just saying that I must be stupid has already been taken as a response. 

Thanks

4Foot

---

### Post by forestpixie on 2008-04-02
Was the unallocated 10Gb inside an extended partition - if so afaik you need to shrink the extended as well so that the spare is out of the extended - then has to be moved so that it's next to the root drive.

can you post the output of 

```
sudo fdisk -l
```

---

### Post by 4Foot on 2008-04-02
> **forestpixie said:**
> Was the unallocated 10Gb inside an extended partition - if so afaik you need to shrink the extended as well so that the spare is out of the extended - then has to be moved so that it's next to the root drive.

can you post the output of 

```
sudo fdisk -l
```

Here is the output you requested.

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d4d57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        9039    57954487+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris
/dev/sda6            3100        8666    44716896   83  Linux

Partition table entries are not in disk order

The 10 gig partition I created is not represented here as the way I left it was in an unallocated state. I can easily make it an extended partition as indicated in my first post but that did not work either. 

Do I read your suggestion to be 1: create the 10 gig as a new extended 3 partition. then 2: Shrink this new partition and then my Sda1 will be able to 'grow' into the now available space?

Thanks for your time

---

### Post by forestpixie on 2008-04-02
No that's not my suggestion.

IF when you run gparted the unallocated space is within the extended area - which I think it is - you have to make the extended partition smaller so that the unallocated space is outside the extended partition. 

Then you should be able to resize the root partition, sda1, to include that space - but it also needs to be next to sda1 in order for you to add the space.

Try using the partition editor on the livecd - then you can post scrnshots if you're not sure.

---

### Post by 4Foot on 2008-04-02
OK Forestpixie, I think I get what you are saying, although "the unallocated space is within the extended partition" has not quite revealed itself to me yet. I will try this in the morning and get back with results. 

There is a new version of GParted out this week which I will try as well.

Thank you very much for the suggestion and the help.

4Foot

---

### Post by forestpixie on 2008-04-02
see attached scrnshot - I have 2 9Gb partitions within an extended partition - if I wanted to add one of them to sda1 - I'd have to get it outside the extended partition before it would be available to add to sda1

Edit - as an aside I've been using parted magic since I had a few problems with gparted - the partition editor looks the same but it's got a few extra things - like firefox
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by 4Foot on 2008-04-05
Thanks very much for your help forestpixie, I appreciate it. I have tried to move, delete, allocate, create and resize that damn partition every way I can without any positive results. I can do all of these things, it is just that my sda1 will not see the available space, extended, unallocated or any which way as available to it for increasing or 'growing' into.

Since I am trying to do this on a small Raptor drive that I use to test any new versions of Ubu before I upgrade my main installation on another drive. And because I have had permissions problems with the sda6 partition since I installed this particular version of Gusty before I upgraded it to Heron I think I will just call it quits for a few weeks until Heron actual arrives.

I will then reformat the drive and start over. I have examined the Parted magic site and documentation and agree that it would seem to be a good alternative to GParted, although the brand new release 3.6.5 of GParted is much better the the older version. I will give Parted Magic a try and from the looks of it, maybe  a few bucks for their kitty would be welcome. 

Thank you for that info and all of your help. You and others like you make this community a great place to be, I look forward to being able to contribute myself someday.

Cheers

4Foot

---

### Post by forestpixie on 2008-04-05
Glad to be of some sort of help - I don't think that gparted is being worked on anymore - read something to that effect here. Good luck when hardy turns up - I'm not having any problems with it - but then I have old hardware.

Everyone makes the community - including you :)

---

