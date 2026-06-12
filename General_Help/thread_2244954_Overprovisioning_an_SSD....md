---
title: "Overprovisioning an SSD..."
date: 2014-09-19
forum: General Help
---

### Post by grndslm on 2014-09-19
(1)  Overprovisioning an SSD is only partitioning a percentage of the SSD (say, 75%)??  ... or using no more than 75% of a drive that has been *fully* partitioned to the max??

(2)  I'm curious how the operating system & hardware communicate with each other in either of these situations.  I've seen some people say that most manufacturers already have 7% of space available for default overprovisioning, but how do we know that Ubuntu actually recognizes this space?  Or how does the drive know what to do with the data that my operating system is moving around?

----

I guess since I've also now seen a couple reviews stating that the more available space you overprovision with (7%, 15%, 25%, etc.) gives more IOPS and gives more credence to the idea that this is specifically in regards to only partitioning, say, 75% of the drive's max capacity.  This is me just reasoning now, but I've seen some conflicting things before in my research.  Not a lot, but enough to make me think that not enough people really know how the SSD's firmware and the OS actually communicate with one another.  I had two SSDs crash a few years back, so I've tried to hold off until now and got the best that money could buy.  But "overprovisioning" was one thing that I did not notice when doing this way back when.  TRIM, firefox and /tmp in ramdisk, vm.swappiness, proper partition block alignment, noatime, etc... but overprovisioning is new science to me.  Anyone know the details?

I think I'm going to repartioning my drive to leave 25% of it unpartitioned, as that looked like it had good results.  I guess if I really need the space in the future, I can just adjust it again.  Never really thought about doing such a thing before.

---

### Post by pqwoerituytrueiwoq on 2014-09-19
i am not sure if that works on every ssd's controller, i know it works on sandforce, but idk about the others
i think that ~7% is hidden from access at the firmware level, leaving space unformatted lets the chip use that in addition to that 7% as far as i know
i don't recall if this improves the iops, i think it makes the drive last longer though
if the unallocated space is to the right in gparted you can extend the partition if needed easily

i did reasurch on ssds for about a week a long time ago

i do use a /tmp ramdisk, i also use a hdd for frequently edited stuff like /var/log and /home and i leave core stuff on the ssd

---

### Post by Cliff_Simonds on 2014-09-20
Copied from [URL="http://en.wikipedia.org/wiki/Write_amplification"]wikipedia:

 [/URL][h=2]Over-provisioning[/h]  [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Over-provisioning_on_an_SSD.png/500px-Over-provisioning_on_an_SSD.png[/IMG]]("http://en.wikipedia.org/wiki/File:Over-provisioning_on_an_SSD.png")

The three levels of over-provisioning found on an SSD.[SUP][[15]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Mehling_Garbage-15")[/SUP][SUP][[20]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Jim_Bagley-20")[/SUP]
 
 
 Over-provisioning (sometimes spelled as OP, over provisioning, or  overprovisioning) is the difference between the physical capacity of the  flash memory and the logical capacity presented through the [operating system]("http://en.wikipedia.org/wiki/Operating_system")  (OS) as available for the user. During the garbage collection,  wear-leveling, and bad block mapping operations on the SSD, the  additional space from over-provisioning helps lower the write  amplification when the controller writes to the flash memory.[SUP][[3]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Lucchesi-3")[/SUP][SUP][[20]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Jim_Bagley-20")[/SUP][SUP][[21]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Drossel-21")[/SUP][SUP][[22]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Smith_2012-22")[/SUP]
 The first level of over-provisioning comes from the computation of the capacity and the use of units of [gigabyte]("http://en.wikipedia.org/wiki/Gigabyte") (GB) instead of [gibibyte]("http://en.wikipedia.org/wiki/Gibibyte") (GiB). Both HDD and SSD vendors use the term GB to represent a *decimal*  GB or 1,000,000,000 (10^9) bytes. Flash memory (like most other  electronic storage) is assembled in powers of two, so calculating the  physical capacity of an SSD would be based on 1,073,741,824 (2[SUP]30[/SUP]) per *binary* GB. The difference between these two values is 7.37% (=(2[SUP]30[/SUP]-10[SUP]9[/SUP])/10[SUP]9[/SUP]  × 100%). Therefore a 128 GB SSD with 0% over-provisioning would provide  128,000,000,000 bytes to the user. This initial 7.37% is typically not  counted in the total over-provisioning number.[SUP][[20]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Jim_Bagley-20")[/SUP][SUP][[22]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Smith_2012-22")[/SUP]
 The second level of over-provisioning comes from the manufacturer.  This level of over-provisioning is typically 0%, 7%, or 28% based on the  difference between the decimal gigabyte of the physical capacity and  the decimal gigabyte of the available space to the user. As an example, a  manufacturer might publish a specification for their SSD at 100 GB,  120 GB or 128 GB based on 128 GB of possible capacity. This difference  is 28%, 7% and 0% respectively and is the basis for the manufacturer  claiming they have 28% of over-provisioning on their drive. This does  not count the additional 7.37% of capacity available from the difference  between the decimal and binary gigabyte.[SUP][[20]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Jim_Bagley-20")[/SUP][SUP][[22]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Smith_2012-22")[/SUP]
 The third level of over-provisioning comes from known free space on  the drive, gaining endurance and performance at the expense of reporting  unused portions, and/or at the expense of current or future capacity.  This free space can be identified by the operating system using the TRIM  command. Alternately, some SSDs provide a utility that permit the end  user to select additional over-provisioning. Furthermore, if any SSD is  set up with an overall partitioning layout smaller than 100% of the  available space, that unpartitioned space will be automatically used by  the SSD as over-provisioning as well.[SUP][[22]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Smith_2012-22")[/SUP]  Yet another source of over-provisioning is operating system minimum  free space limits; some operating systems maintain a certain minimum  free space per drive, particularly on the boot or main drive. If this  additional space can be identified by the SSD, perhaps through  continuous usage of the TRIM command, then this acts as semi-permanent  over-provisioning. Over-provisioning often takes away from user  capacity, either temporarily or permanently, but it gives back reduced  write amplification, increased endurance, and increased performance.[SUP][[17]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Layton-17")[/SUP][SUP][[21]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Drossel-21")[/SUP][SUP][[23]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-Anand_Spare_Area-23")[/SUP][SUP][[24]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-24")[/SUP][SUP][[25]]("http://en.wikipedia.org/wiki/Write_amplification#cite_note-25")[/SUP]
   [TABLE="align: center"]
**Over-provisioning calculation** [TR]
 [TD][IMG]http://upload.wikimedia.org/math/1/e/2/1e20844b6c83913c2a9bb6c376e01995.png[/IMG][/TD]
[/TR]
[/TABLE]
[URL="http://en.wikipedia.org/wiki/Write_amplification"]
[/URL]

---

### Post by mcduck on 2014-09-20
1. I'm not sure what's the question here. I'd say if you want to maximize the drive's lifetime, then it doesn't really make much difference if you partition all of the drive but never fill it up to 100%, or if you just leave some of the space unpartitioned. 

2. The OS doesn't care, or even know, about the overprovisioning that happens at the drive level, the controller chip on the drive itself keeps track of it, and maps any reads & writes automatically. (It's pretty much the same with magnetic hard drives these days, the controller on the drive keeps track of reads and writes, and using buffer memory on the drive re-arranges all reads and writes for best speed, caches recently used data, handles reallocating bad sectors (or overprovisioning) and so on without the OS ever knowing about it. What actually happens on the drive is pretty much abstracted away by the drive controller.

---

### Post by grndslm on 2014-09-20
I'm not quite sure what the question is either.  :)  I just want to understand what is really happening behind the scenes, and what is the right choice to make when it comes to overprovisioning, esp. considering I've had 2 failed SSDs in the past (OCZ Vertex 32gb _and_ Sandisk 128GB).

Anyway, like I said, I've seen conflicting information that overprovisioning is automatic whether you "partition all of the drive but never fill it up to 100%, or if you just leave some of the space unpartitioned".  And I just want to make sure.  I'd actually already partitioned the drive out fully, as I would always do.... before coming across this information, so I'm just going to boot into a thumb drive and readjust the partitions.  Case closed.

Whole thing that really makes me think that the drive controller is doing something a bit more than the OS is this review --> [http://www.anandtech.com/show/8216/samsung-ssd-850-pro-128gb-256gb-1tb-review-enter-the-3d-era/7](http://www.anandtech.com/show/8216/samsung-ssd-850-pro-128gb-256gb-1tb-review-enter-the-3d-era/7)

Those are huge gains realized at 25% of the drive being left unpartitioned, so I think I'll stick with that.  :)  Plus, I don't want any more SSDs to crash.  Hopefully a 10-year warranty on this drive will be good enough.

I still don't quite understand how the drive controller recognizes there is unpartitioned space available for it to use, but I guess I can really go without the answer.  The review should really be all I need to know.  Plus, adjusting a logical partition to expand available space in the future is really not difficult at all.  So it's really a non-issue if it provides faster speed and better reliability.

---

### Post by mcduck on 2014-09-20
The partitions are just an illusion, the controller has it's own way of managing the data and how much space each "partition" on the drive has available, so it's able to make things appear to the OS as if the drive was actually split into partitions with set boundaries  while at the same time it internally ignores any actual partition boundaries, and instead distributes the data across all available space (even the parts that might not ever be reported to the operating system). 

Because of this it makes no difference if the empty space is partitioned, or unpartitioned, or even exists on a different partition. As long as there is enough unused space on the drive, the controller is able to spread the data around and keep read/write cycles on each data block as small as possible.

(like I said, all hard drives do similar abstraction between reported and the actual data storage on the device. Magnetic hard drives will report the disk surface to the computer using the old cylinder/sector/head values, but actually use the disk surface in more efficient way that allows using more of the surface to store data, with the controller mapping the data between reported and actual locations on the disk surface)

---

### Post by grndslm on 2014-09-20
That all makes sense, except for the whole point AnandTech makes about a greater amount of overprovisioning yielding a much greater rate of IOPS.

How does the controller work faster with a greater amount of overprovisioning, versus fully partioning the drive but never filling it up past 75%?

Here is the article I'm talking about, in case you missed it... [http://www.anandtech.com/show/8216/samsung-ssd-850-pro-128gb-256gb-1tb-review-enter-the-3d-era/7](http://www.anandtech.com/show/8216/samsung-ssd-850-pro-128gb-256gb-1tb-review-enter-the-3d-era/7)

---

