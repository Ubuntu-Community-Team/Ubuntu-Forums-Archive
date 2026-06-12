---
title: "Partitioning"
date: 2008-07-08
forum: General Help
---

### Post by JR Tyner on 2008-07-08
This is the first time I've installed a Linux OS. Before now I have used Live CDs or a computer that already had a Linux OS installed.

I want to install Xubuntu on my 12GB USB MicroDrive so that I can plug it into a PC and boot Xubuntu, and never have to sit though Vista restarting Windows Explorer again.

I think the MicroDrive needs to be partitioned like this:

/dev/hda1 -- /boot (100MB)
/dev/hda2 -- / (10GB)
/dev/hda3 -- swap (1GB)
/dev/hda4 -- /home (900MB)

What should I partition each partition as?

Can someone guide me step by step, I'd rather only have to do this once without me screwing up.

---

### Post by Elfy on 2008-07-08
If you're not going to be worrying about upgrading the install I wouldn't be worrying about a seperate home, especially if you are expecting to only use less than 1Gb you could just copy it onto a couple of cd's to back it up.

Nor would I worry about a seperate /boot, in fact I'd probably just have / and swap on there.

---

### Post by JR Tyner on 2008-07-08
I figured the numbers might be a little off. I got them by scaling down some numbers my friend James left me for installing Ubuntu on my Laptop. 

I have the home partition because I will upgrade it, but I didn't think it needed to be as big for Xubuntu.

---

### Post by Elfy on 2008-07-08
The home partition is where your data and configs will live, so 900Mb is not a lot - regardless of whether you are going to upgrade or not, if that is all the space you're going to be using I would just have / and back it up when needing to reinstall.

---

### Post by JR Tyner on 2008-07-08
So how about this:

I partition 2GBs as swap, what do I partition the rest as?

---

### Post by Elfy on 2008-07-08
Leave it as / - it will still have a /home but it will be in / rather than in a seperate partition. You doubled the size of swap then :)

---

### Post by JR Tyner on 2008-07-08
No I mean when it asks what system do I want to partition it as, which do I select from the drop down menu?

What all is the swap partition used for?

---

### Post by Elfy on 2008-07-08
Sorry misunderstood :) - ext3 is default I think, at least that is what I have.

The swap partition is similar to the win pagefile

---

### Post by JR Tyner on 2008-07-08
So it's like the pagefile, then 3 GB might be more appropriate.

---

### Post by Topsiho on 2008-07-08
My two penny's is that swap should be twice your RAM-memory.
Secondly you need not have so much space for your system (/ directory), let's say 6 GB is quite enough unless you install tons and tons of programs, and of course Gnome and KDE desktops as well.
The remaining space you can use for your /home directory, space in which your documents, photo's, and .iso's and other downloads will come, and of which you ***never*** have enough. When upgrading or so you can have /home not being formatted and so keep your stuff (and settings) intact.

Topsiho

---

### Post by JR Tyner on 2008-07-08
Wait, I got 2 GB ram, and a little over 6 GB worth of programs to install, not counting Xubuntu or WINE.

I am using the MicroDrive so that I can plug it in where ever I am, surf the net, check my mail, and play my games with out using Vista.

---

### Post by JR Tyner on 2008-07-08
[IMG]http://img.photobucket.com/albums/v617/bluefrogk0e/bumpjar.gif[/IMG]

---

### Post by bluepowder7 on 2008-07-08
> **JR Tyner said:**
> Wait, I got 2 GB ram, and a little over 6 GB worth of programs to install, not counting Xubuntu or WINE.

I am using the MicroDrive so that I can plug it in where ever I am, surf the net, check my mail, and play my games with out using Vista.

a) set aside 2G for /swap (which is filesystem type swap), and put the rest as /(root) using either JFS or XFS - they'll give you more useable space than ext2/3 (xfs gives most, jfs slightly less, ext2/3 quite a bit less)

b) hang on - you plan on plugging this into a wide variety of not-at-all-similar computers?  i'm not sure how well that is going to work.  are you thinking of having the linux-equivalent of vista's readyboost?

---

### Post by JR Tyner on 2008-07-08
> **bluepowder7 said:**
> a) set aside 2G for /swap (which is filesystem type swap), and put the rest as /(root) using either JFS or XFS - they'll give you more useable space than ext2/3 (xfs gives most, jfs slightly less, ext2/3 quite a bit less)

b) hang on - you plan on plugging this into a wide variety of not-at-all-similar computers?  i'm not sure how well that is going to work.  are you thinking of having the linux-equivalent of vista's readyboost?

A) So only 2GB not 3 for Swap, and a 10GB / partition as xfs? Will this give me the greatest read speed? I'd like to minimize any lag  with playing games off of it. 

B) Short version = Yes. I plan to boot off of it while at friends' houses where they don't have Linux, and I'm unsure how clean their system is.

---

### Post by bluepowder7 on 2008-07-08
a) yeah, 2g swap should be enough.  as for speed, you can tune filesystems to get max transfer speeds, and since you're on a flash drive and not a "spinning platter with moving heads" hard drive, speeds should be quite fast anyways.  xfs will simply give you access to more of what little space you do have.  do some reading on the filesystem space efficiency - i think xfs was something like 99.9%, jfs was 99.3%, and ext2/3 were around 90% (so your 10G would actually be 9.99G, or 9.93G, or 9.0G)

b) can't answer that.  i have a feeling that it won't work all that easily since there will be a whole different set of processors, drivers, etc.  though, hmm, sounds like what you want to have is a flash-drive version of a LiveCD that works on any computer.  maybe that IS possible?

---

### Post by JR Tyner on 2008-07-08
Here's a little more about the drive, in case it helps:

Product Features

    * High Capacity and Tiny Size
    * Internal 1" Hard Drive
    * 180 Degrees Rotational USB Interface
    * Blue LED Denotes Power and Flashes with Disk Activity
    * High-Speed USB 2.0 Interface 
    * Works with Windows, Mac and Linux OS
    * 1 Year Manufacturer Warranty 

Product Specifications

    * 12 GB Capacity
    * Aluminum Case
    * 3,600 rpm drive speed
    * Sustained Data Transfer Rate - 8.8MB/sec
    * Weight (12 GB) - 1.2 ounces
    * Dimensions (12 GB) - 75 mm (W) x 33 mm (H) x 10 mm (D) 

I'm sure the drive speed and Data Transfer Rate are important to what I want to do.

---

### Post by JR Tyner on 2008-07-08
> **bluepowder7 said:**
> a) yeah, 2g swap should be enough.  as for speed, you can tune filesystems to get max transfer speeds, and since you're on a flash drive and not a "spinning platter with moving heads" hard drive, speeds should be quite fast anyways.  xfs will simply give you access to more of what little space you do have.  do some reading on the filesystem space efficiency - i think xfs was something like 99.9%, jfs was 99.3%, and ext2/3 were around 90% (so your 10G would actually be 9.99G, or 9.93G, or 9.0G)

b) can't answer that.  i have a feeling that it won't work all that easily since there will be a whole different set of processors, drivers, etc.  though, hmm, sounds like what you want to have is a flash-drive version of a LiveCD that works on any computer.  maybe that IS possible?

A) How do I tune filesystems?

B) Yes, a USB version of a LiveCD is what I want.

---

### Post by bluepowder7 on 2008-07-08
a) ooh, you're using a microdrive (or similar).  well, that will make tuning the filesystem quite a bit more important, especially since the spindle is only going at 3600rpm, compared to a typical 5400rpm or 7200rpm hard drive (actually, i don't know if 5400's are still made).  anyhoo, i have never done a filesystem tune, so do a search.  i do recall there was a web article on tuning xfs.

[http://everything2.com/index.pl?node_id=1479435](http://everything2.com/index.pl?node_id=1479435)

---

### Post by JR Tyner on 2008-07-08
T.One USB Microdrive: [http://www.thinkgeek.com/computing/drives/8714/](http://www.thinkgeek.com/computing/drives/8714/)

Looks like this will be harder than I thought.

---

### Post by bluepowder7 on 2008-07-08
well, at least the partitioning thing is sorted out!  now all that's left is the tuning (if it's even needed - maybe try it with defaults first), and the LiveUSB thing.  that might need a new thread with the appropriate subject line.  or more web searches...

---

### Post by JR Tyner on 2008-07-09
When I made the root partition it said the rest of the drive was unusable and wouldn't allow me to make a swap partition.

At the end I got "Executing 'grub-install (hd10)' failed This is a fatal error."

---

### Post by JR Tyner on 2008-07-09
[IMG]http://img.photobucket.com/albums/v617/bluefrogk0e/bumpjar.gif[/IMG]

---

### Post by bluepowder7 on 2008-07-09
i guess you're using the built-in GParted utility?  i've had quite a few snags with it, but the one way that generally seems to get things done is to do one thing at a time.

remove partition
apply
remove other partition
apply
remove whatever other partition is left
apply
make ONE partition
apply
make another partition
apply
do something else
apply

and so on and so on...  i found that sometimes, i even need to close and restart GParted after blowing away all the partitions, or after 2-3 applies.  long-winded, but tends to work.

---

### Post by JR Tyner on 2008-07-11
I ended up wiping out Windows. I had planned on doing that eventually, but not till I decide whether I want to use Ubuntu or Kubuntu. All I lost was my Firefox bookmarks and my Thunderbird settings.

I got the partitions on the USB MicroDrive, but I still haven't managed to get it to work.

---

