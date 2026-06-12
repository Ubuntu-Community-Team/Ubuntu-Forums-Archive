---
title: "only 270 gigs from 320g hard drive"
date: 2008-02-22
forum: General Help
---

### Post by JimBuntu on 2008-02-22
why is it that I install a brand new 320g hard drive and Ubu only shows 270, Not to mention it shows 17g already used and I have not saved anything on this comp yet?

---

### Post by soldats on 2008-02-22
if you do an "sudo fdisk -l" does it show any other partitions on it?

---

### Post by rapiscan on 2008-02-22
Your OS will always list the harddrive as smaller than the advertised size.  This is because manufacturers have decided to use a base-10 representation of a gigabyte instead of a base 2 representation (which is what computers use).

In base 2, 1 GB == 1,073,741,824 bytes
In base 10, 1 GB == 1,000,000,000 bytes

Therefore, the hard drive size "appears" smaller in base 2.  If I'm not mistaken, hard drive manufacturers have been sued over this in the past.

---

### Post by monte48lowes on 2008-02-22
If you have formatted the drive as 'ext3' then a small percentage of the filesystem is saved for 'root' and will not be shown as available. This is necessary on a system so that if a user fills the disc root will still be able to use it.

Mike

---

### Post by dcstar on 2008-02-23
> **monte48lowes said:**
> If you have formatted the drive as 'ext3' then a small percentage of the filesystem is saved for 'root' and will not be shown as available. This is necessary on a system so that if a user fills the disc root will still be able to use it.

Mike

EXT3 has an overhead for the journal, this is included in the reserved root area.

Anyone desperate for additional space can convert the EXT3 to EXT2, you gain space but you lose all of the advantages of journaling.

Other filesystem types such as ReiserFS may be worth looking at for the various trade-offs of available space, performance and resilience (I use ReiserFS for my VMware partitions as the performance is better than EXT3, and the resilience is almost as good).

---

### Post by JimBuntu on 2008-02-24
your telling me that it takes 60 gigs of space to do all this.

---

### Post by coastdweller on 2008-02-24
> **JimBuntu said:**
> your telling me that it takes 60 gigs of space to do all this.

I believe the installer decides the other partitions based on percentage.

For example, I would assume (If i was right) that a 32 gb drive would use 6gb.

Hence, your 320gb spares out 60. 

Just a thought.

---

### Post by dcstar on 2008-02-24
> **JimBuntu said:**
> your telling me that it takes 60 gigs of space to do all this.

You should read the earlier posts about sizes.

Ubuntu reports my "160GB" drive as 149.05GiB, so your "320GB drive will be reported as ~298Gib total.

As for the partition you are referring to, that depends entirely how big the partition is, not the drive size.

---

### Post by jeffus_il on 2008-02-24
Run parted in a terminal.
At the parted prompt type p ```
(parted) p
```and post the output.
Here is mine for a 160Gb disk:
```
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  5001MB  5001MB  primary   reiserfs     boot 
 2      5001MB  11.0GB  6004MB  primary   reiserfs          
 4      11.0GB  160GB   149GB   extended                    
 5      11.0GB  32.0GB  21.0GB  logical   reiserfs          
 6      32.0GB  84.4GB  52.4GB  logical   reiserfs          
 7      84.4GB  137GB   52.4GB  logical   xfs               
 8      137GB   138GB   1045MB  logical   linux-swap      
```

---

### Post by JimBuntu on 2008-02-24
I'm new to using terminal, so, is that all i type in? or do i need the word sudo or anything??

---

### Post by jeffus_il on 2008-02-25
> **JimBuntu said:**
> I'm new to using terminal, so, is that all i type in? or do i need the word sudo or anything??
No sudo needed, since you are only reading, no updating or writing.

---

