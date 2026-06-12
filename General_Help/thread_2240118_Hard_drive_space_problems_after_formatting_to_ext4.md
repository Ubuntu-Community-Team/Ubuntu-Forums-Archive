---
title: "Hard drive space problems after formatting to ext4"
date: 2014-08-18
forum: General Help
---

### Post by howeishotweb on 2014-08-18
Hello,
After installing Ubuntu I have begun converting my four hard drives from NTFS to ext4, beginning by wiping the biggest one clean, and then moving stuff over so I can format the rest. But I am already unable to do so with the second harddrive...

Lets call them
HDD1 and HDD2.

HDD1 was the big one that got wiped clean and formatted to ext4. I then moved everything from then-NTFS formatted HDD2 over on it, and formatted HDD2 to ext4. HDD2 only had two folders of data. The first folder went back to HDD2 fine, but when trying to copy the second folder, there is suddenly not enough disk space.

I see that Ubuntu reports HDD2 to be 492.1 GB. The first folder is 11,5 GB, which should leave 480.6 GB of free space. But Ubuntu says there is only 455.5 GB of free space, which is insufficient for the rest of the data, as the second folder is 477.5 GB.... Where did all that space go??
25.1GB of space disappeared into thin air.

(another small strange thing I noticed was that after formatting HDD1 to ext4, Ubuntu said there was already used 70MB... what is that, I wonder).

---

### Post by mcduck on 2014-08-18
By default, Ext4 reserves 5% of the space for root user only. This is needed on system drives to ake sure normal suer's can't fll the drive to the point where the operating system wouldn't be able to create ceetain run-time files it needs t boot and run correctly.

Of course the 5% is a bit of an overkill with the large hard drives we have these days, and if it's a storage drive it probably isn't necessary to reserve any space at all (although Ext does start to suffer from file fragmentation if the drive gets too full, so you really wouldn't want to fill them up to 100% anyway).

You can change the amount of reserved space using the *tune2fs* command. For example, assuming the filesystem you wan to change is on sdb1, and you wish to completely remove the reserved space:
```
sudo tune2fs -r 0 /dev/sdc1
```

(You will, of course, still loose some of space on the drive for things the filesystem itself needs, like the journal, but that shouldn't be a big difference in overhead compared to NTFS so unless your drive was absolutely full packed with data, it shouldn't be a problem)

---

### Post by howeishotweb on 2014-08-18
Thank you for your reply. That makes sense, good to know to think about those 5%. I will try to shuffle my data around before changing the reserved space, I'm sure I can get it to fit.

---

### Post by stalkingwolf on 2014-08-18
is it possible that it is a difference in how it reads a GB?  a few years ago i ran across an article and a thimb drive that said some manufacturers were changing the standards
from 1gb being 1024 to 1000 mb.

never saw anything more.

---

### Post by JKyleOKC on 2014-08-18
> **stalkingwolf said:**
> is it possible that it is a difference in how it reads a GB?  a few years ago i ran across an article and a thimb drive that said some manufacturers were changing the standards
from 1gb being 1024 to 1000 mb.

never saw anything more.No drive manufacturer I've ever seen has used anything other than decimal when speaking of storage space. To them, a kilobyte is 1,000 bytes, not 1,024. Similarly all the way up, and by the time they get to a gigabyte the difference is quite a few megabytes!

Meanwhile most disk management programs report using binary-based units, leading to some rather heated discussions. There's a not-very-loud movement under way to add an "i" in the middle of the unit abbreviation, to remove some of the confusion, but it doesn't seem to be well accepted yet.

Here's a little table I put together to help me make the conversions:```
Mfr Rating	Programs	Actual Bytes
1 KB		.98 KiB		1,000
1.02 KB		1 KiB		1,024
1 MB		.95 MiB		1,000,000
1.05 MB		1 MiB		1,048,576
1 GB		.93 GiB		1,000,000,000
1.07 GB		1 GiB		1,073,741,824
1 TB		.91 TiB		1,000,000,000,000
1.1 TB		1 TiB		1,099,511,627,776

```
In this case, though, I think the 5% safety factor is what's causing the problem...

---

### Post by mcduck on 2014-08-18
> **JKyleOKC said:**
> No drive manufacturer I've ever seen has used anything other than decimal when speaking of storage space. To them, a kilobyte is 1,000 bytes, not 1,024. Similarly all the way up, and by the time they get to a gigabyte the difference is quite a few megabytes!


Pretty much all of them did, up to the point when drives reached gigabyte sizes. I suppose at that point the storage space become large enough that nobody had to care if the size fits exactly with the way the computer actually uses the data. (and the connection between that and the file sizes and space the file uses on the drive became distant enough for most users so magnetic drive manufacturers could easily switch to using 1000 as the multiplier)

Also it should be noted that sizes of SSD drives, memory cards etc. are still often using the 1024 multiplier, as that's what you get when combining together the memory chips used in them.

I still have some of my old hard drives around, including a 8MB one (the label stating it's 8 MB / 8388608 B) and a fair bet more new 256 MB one ( label states 268435456 Bytes). I'm pretty sure even the 8GB drive I should have somewhere around was labelled and sold with 1024 as the multiplier. After that all the magnetic drives I've bought started using the 1000 as multiplier.

---

### Post by JKyleOKC on 2014-08-18
Well, you're absolutely correct about the 8-MB drive using 1024 as the multiplier. I didn't pay much attention to these details until drives got up into the gigabyte region, even though I worked for 24 years writing service manuals for maintrame drives at G-E/Honeywell/MPI. By that time it seemed to be almost universal to use decimal notation, driven, I suspect, by the marketeers rather than the engineering staff.

There always has been a slight discrepancy, though; manufacturers almost universally have rated drive capacity on the basis of "unformatted" byte count, but the low-level formatting required to break a track up into sectors does take away some of that capacity, with the result that almost no storage management program could ever report as much space on a drive as the manufacturer claimed!

Back in the days of the floppy disk (5-inch variety, no less) I was told by one of the design engineers that the structure I was getting on the disk wasn't physically possible, because of that low-level format (quite different from file-system formatting) required. The program itself, however, didn't put as much blank space between sectors as the engineers felt to be necessary, and thus could squeeze one extra sector into each track!

We've certainly come a long way in the past 50 years!!!

---

### Post by mcduck on 2014-08-18
> **JKyleOKC said:**
> 
We've certainly come a long way in the past 50 years!!!
+1 to that. It's pretty insane to even compare the large 8MB hard that used to be my system drive back in the days (and pretty much the only storage I had, apart from piles of floppy disks...), and the 64GB MicroSD card I have in my phone now just to keep my music collection always with me. :D

---

