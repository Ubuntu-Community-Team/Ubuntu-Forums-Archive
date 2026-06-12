---
title: "media server questions, LVM vs Raid vs??"
date: 2008-01-27
forum: General Help
---

### Post by troutbum13 on 2008-01-27
I am replacing a POS WHS, with a gutsy server, and I am a little confused about the best way to go, I currently have 1TB of media files split across multiple HDDs. I want to be able to serve up a single smb share that spans multiple HDDs on the back end, I also would like to be able to add new disks as the media collection grows...I am on the fence about redundancy in the array 
, read and write speeds are also important (that is why WHS is getting the boot).  So any opinions on how to go about it? LVM, software raid. I know next to nothing about either of them.

I have 
3 identical 500GB sata drive
2 36GB raptor (thinking of running the root separate from the shares on one or both of these)
1 500GB pata drives
2 200GB pata drives

thanks for any and all help
alec

---

### Post by danwood76 on 2008-01-28
One way to do it would be to buy a descent RAID card and setup a RAID 5 array.
The only real problem you have is that you have various sized disks, for the ideal setup you need 3 or more of the same disks to give maximum performance.
I notice you have 3 500GB disks which will serve a RAID 5 well.

With most descent RAID 5 cards tehy allow for dynamic resizing of RAID 5 arrays allowing you to add more 500 GB disks at a later time. Though you need to make sure that the RAID card can support resizing of the volume size you wish to create, and is also supported under linux.

regards,
Danny

---

### Post by sandwormblues on 2008-01-30
raid 5 is going to be really slow for a media server.  or is it just going to be a file server?  raid 0 is your best bet for a media server

---

### Post by bigredradio on 2008-02-13
Raid and LVM are very different and are for different purposes. What do you want to get out of it?

Also, having different sized disks is not an issue. You can build your raid devices using software raid on partitions.

Do you want redundancy, speed, or just trying to utilize all of your storage efficiently? Building filesystems on partitions is very inflexible because you always run out of space in one filesystem, while there is available space in another. Also, most make the mistake of creating one big partition and a swap partition. This is worse.

LVM allows you to lump all of your storage together so that it can appear as one or more devices no matter how many REAL disks you have.

RAID is better suited for redundancy (RAID 1) and speed (RAID 0) than it is for storage consolidation. You can also build LVM on top of RAID or visa-versa. This can give you the best of both worlds.

Since your OS can run on a 36GB disk very comfortably, I assume the rest is media space. Corrupt filesystems can be repaired, but only if you can get access to the OS. 

Use RAID1 to mirror the two root disks. Then use LVM to consolidate the rest of your storage into one or more volume groups.

There are a number of how-to's, but if you decide to go this route and run into trouble let me know. I am thinking of doing a talk on LVM and this would give me an excuse to write a how-to. There are a number of ways you can utilize this space. It comes down to your priorities. If you have to have redundancy, then RAID + LVM would be my choice.

---

### Post by troutbum13 on 2008-02-17
thanks, I 'll let you know if I run into any issues.

---

### Post by Chipmaster on 2008-02-27
Does LVM provide any benefits if you are only going to have a single partition on a device?  I'm looking to do something similar to the OP, but my raid will only have one partition on it as I have a separate disk outside the raid that has my /, /boot, /home, /usr, and /tmp partitions.

---

### Post by bigredradio on 2008-03-20
Probably not if you are never going to need more space and only want one partition. However, I remember getting my first 4GB hard drive and thinking I would never fill that thing up. :)

---

