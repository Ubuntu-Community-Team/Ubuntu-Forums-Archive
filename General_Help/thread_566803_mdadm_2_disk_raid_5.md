---
title: "mdadm 2 disk raid 5"
date: 2007-10-03
forum: General Help
---

### Post by lirelent on 2007-10-03
I've created a 2 disk raid 5 with mdadm,  I choose raid 5 instead of raid 1 because I wanted to be able to add a third disk in the future and just grow the raid and have the 1 disk overhead advantage of raid 5.  Some sysadmins that I know INSIST that this is an IMPOSSIBLE setup and warn me that if I lose a disk and if the raid is over ~80% full I will LOSE data and I would also be unable to rebuild the array with a replacement disk.  I'm fairly convinced that this is not the case, based on what I know about how raid 5 works, also by the fact that mdadm didn't post any warning when I created the raid.

What I want to know from someone of authority is, would or wouldn't I lose data or be able to rebuild the array?

thank you.

---

### Post by brydonhunter on 2007-10-04
In order to have raid 5 you need a minimum of three disks. The idea is that one disk is "lost" from the total disk storage, 3 x 500Gb = 1 TB. In very basic terms, the data will be written to two of the disk with a checksum on the third. This is done in a fashion that if one of the disks fails, the raid can be re-constructed from the remaining data. Of course there is a lot more to this than what I have written but in a nutshell...

Just because mdadm did not complain, it does not mean that you have a true raid 5. If somehow mdadm made a "virtual" raid 5 configuration, it will fail simply by the nature of true raid 5. I would not trust this setup even if it does work.

Do you have any info on mdadm creating raid 5 with two disks? It would be interesting to see this.

Hope this helped and good luck!

---

### Post by brydonhunter on 2007-10-04
From the mdadm man page:

<quote>
To  create a "degraded" array in which some devices are missing, simply give the word "missing" in place of a device name.  This will
       cause mdadm to leave the corresponding slot in the array empty.  For a RAID4 or RAID5 array at most one slot can be "missing"
</quote>

So yes you can create a raid 5 with only two disks but it will be in degraded mode meaning that the structure may be setup as raid 5 but it is not running in true raid 5 at that moment. It is like having one disk fail, the raid will continue to work and rebuild itself once the new disk is inserted. The problem is, if another disk fails, all data is lost.

Unless you are planning on purchasing a new disk VERY soon, I would not do this... too risky.

---

### Post by lirelent on 2007-10-04
FIrst of thank you for replying to my thread, but I do have a few questions, I'd just like to understand better what's going on here (the engineer in me)

As far as the "missing" drive is concerned
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Aug  3 21:05:33 2007
     Raid Level : raid5
     Array Size : 488383936 (465.76 GiB 500.11 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct  4 12:51:17 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 036304da:66fe5f8d:5aef842c:eea454f8 (local to host endeavor)
         Events : 0.120

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

If I read that correctly it is a raid 5 with 2 devices and none "missing", right?

Also my thought about why a 2 disk raid 5 should work, is that raid 5 is distributed parity, so in a 2 disk raid 5 for each bit you'd have one parity bit (assume even parity).
So if my data bit is 1 my parity bit would also be 1.
If I lost the drive with the data bit, from the parity bit of 1 i KNOW that the missing data bit was a 1.

Also as an experiment I unplugged the data cable on one of the drives, and I was still able to read all my data just fine, my sysadmin friends say that this is because my drive is <80% full, but I'm not sure why that would matter considering the distributed nature of raid 5.

So if you could point out the flaw in my logic I would really appreciate it (the engineer in me at least).

Again thank you for the input.

---

### Post by psusi on 2007-10-04
How full the filesystem is has nothing to do with anything.  Once the array fails, you will not be able to read any data from it at all.  

The 2 disk setup that you describe is essentially raid1, not raid5.  In other words, every data bit on the primary drive is copied exactly to the other drive.  If raid1 is what you wanted, then that's the type of raid you should request.  By the way, how large are these disks?  500 gigs?   If so then it looks like that is indeed what mdadm has done; just set it up as a mirror for now.

---

### Post by mjwood0 on 2007-10-06
The problem with not having 3 disks in a RAID 5 array is as follows:

Typical RAID 5 (3 x 90 GB drives)
----------------------------------------
[FONT="Courier New"]DISK 1 - 30 GB Orig Data 30 GB Mirror Data  30 GB Parity Data
DISK 2 - 30 GB Mirror Data  30 GB Parity Data  30 GB Orig Data
DISK 3 - 30 GB Parity Data  30 GB Orig Data    30 GB Mirror Data
TOTAL SPACE = 90 GB[/FONT]

This isn't technically the quantity of data stored on each disk, but the idea is correct.  (In actuality, parity data takes up less space on these drives if I remember correctly, but proportions aside, this is the general idea)

What you will notice is that if one disk crashes, you have at least two copies of orig data, two copies of mirror data and two copies of parity data.  This is enough to re-build your whole 90 GB of data.

If you put three partitions over 2 drives, you are eliminating one of the redundant failure points and therefore, if one drive crashes, you won't be left with enough data to fully repair your array.  Remember, drives usually don't die a partition at a time -- they die a whole drive at a time.

In your case, it seems better to create a RAID 1 array -- two mirrored copies of the same data.  While there won't be a performance gain, if you really wanted that you'd want a hardware raid solution not a software solution anyway.

Just my $0.02.

---

### Post by bobpaul on 2007-10-24
> **lirelent said:**
> I've created a 2 disk raid 5 with mdadm,  I choose raid 5 instead of raid 1 because I wanted to be able to add a third disk in the future and just grow the raid and have the 1 disk overhead advantage of raid 5.  
 ... SNIP ...
What I want to know from someone of authority is, would or wouldn't I lose data or be able to rebuild the array?

What you're doing is perfectly acceptable. Though I would recommend you do a mirror now and convert it later (see here [http://www.n8gray.org/blog/2006/09/05/stupid-raid-tricks-with-evms-and-mdadm/](http://www.n8gray.org/blog/2006/09/05/stupid-raid-tricks-with-evms-and-mdadm/) ) for instructions. EVMS not required you're fine.

The way raid5 functions is to stripe all of your data across N-1 drives and use the last drive for XOR parity. The parity is also striped. That is to say, if N is 3 drives, you'll have the following
```
       **Drive1**  **Dive2** **Drive3**
Block1:  A1     A2    P1
Block2:  B1     P2    B2
Block3:  P3     C1    C2
Block4:  D1     D2    P4
Block5:  B1     P5    B2
```

and so forth. Here A1, A2 etc are blocks of stripped data. P1, P2, etc are the parity for that stripe set. You can loose A1, A2, or P1, but not 2 or more. P1 is calculated as P1 = A1 XOR A2; 

If you're using just 2 disks in a **non-degraded** setup, then you'll have the following structure
```
       **Drive1**  **Dive2**
Block1:  A1    P1
Block2:  P2    B1
Block3:  C1    P3
Block4:  P4    D1
```

In this case, you're parity blocks will actually be identical to your non-parity blocks. This is because P1 is calculated as P1 = A1 XOR ?? Since there is no other block to XOR your bits with, md falls back to ?? = 0, and we all know that the XOR of 0 is the identity. That is, P1 = A1 XOR 0 == A1

In this case, you're simply using the RAID5 mode of the md driver to construct a mirror, and there is no difference between your 2 disk RAID5 and an actual mirror. You're sysadmin friend doesn't know what he's talking about, and most of the others in this thread seemed to miss what you were trying to do. They were, however, wise to point out that a degraded 2 disk raid 5 (ie, raid5 on 3 disks with 1 missing) is essentially a striped array and is no good.

If you have any doubts, google is your friend. When I was first looking about converting Raid1 to Raid5 I found some back posts on the kernel mailing list or possibly an mdadm specific mailing list that spoke of doing the same thing as the "stupid raid tricks" link I posted. I've since successfully completed the conversion with a live system and no data loss. Gotta love hotswap bays ;)

---

### Post by bobpaul on 2007-10-24
> **mjwood0 said:**
> The problem with not having 3 disks in a RAID 5 array is as follows:

Typical RAID 5 (3 x 90 GB drives)
----------------------------------------
[FONT="Courier New"]DISK 1 - 30 GB Orig Data 30 GB Mirror Data  30 GB Parity Data
DISK 2 - 30 GB Mirror Data  30 GB Parity Data  30 GB Orig Data
DISK 3 - 30 GB Parity Data  30 GB Orig Data    30 GB Mirror Data
TOTAL SPACE = 90 GB[/FONT]


That's not RAID 5. I'm not sure what that is, but it most definitely is not RAID 5. RAID5 does not include any mirroring; only striped data and parity blocks. If you have 3x 90GB drives you'll have a 180GB array with 90GB of data scattered across the 3 drives of Parity. The parity is used to reconstruct missing blocks should a drive failure be encountered.

**[Edit]** You can learn about raid levels here: [http://www.acnc.com/04_01_05.html](http://www.acnc.com/04_01_05.html)

---

