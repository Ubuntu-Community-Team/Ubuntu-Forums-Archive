---
title: "which filesystem?"
date: 2008-02-25
forum: General Help
---

### Post by djbsteart1 on 2008-02-25
Is there any real noticeable difference between the filesystems ubuntu offers, obviously, there is with ext2 and the others, but jfs, xfs, reiserfs and ext3. is there a preference? or are all of them reat in there own right?

---

### Post by jeffus_il on 2008-02-25
> **djbsteart1 said:**
> Is there any real noticeable difference between the filesystems ubuntu offers, obviously, there is with ext2 and the others, but jfs, xfs, reiserfs and ext3. is there a preference? or are all of them reat in there own right?

No there is no noticeable difference, (for normal people), use the most popular, probably ext3, some are a bit better for large files, others for small ones, some use more cpu, others are heavier on disk i/o. Choosing a better file system will not convert your desktop Ford Model T into a Porshe!

---

### Post by djbsteart1 on 2008-02-25
i wasnt wanting a porsche, i guess that coming from ntfs anything linux has to offer will be good. i can just remember reading that one was very fast compared to the others. which one is it that uses less cpu, as that is in high demand on my system?

---

### Post by articpenguin on 2008-02-26
> **djbsteart1 said:**
> i wasnt wanting a porsche, i guess that coming from ntfs anything linux has to offer will be good. i can just remember reading that one was very fast compared to the others. which one is it that uses less cpu, as that is in high demand on my system?

thats JFS

---

### Post by seventhc on 2008-02-26
I use reiserfs for my boot partition (read that it's faster) and ext3 for everything else, not including swap of course.
I Think ext3 is an improvement over ext2 so I would use ext3. From what I've read, I think ext2 fragments more than ext3.
So If your only going to use on file system and a swap ext3 is the way to go.

---

### Post by articpenguin on 2008-02-26
ext3 is ext2 with a journal nothing more. Ext2 is inspired by a 20 or 30 year old filesystem called FFS i think. 


all filesystems fragment, some fragment less some fragment more. All linux filesystems fragment less then ntfs/fat

---

### Post by djbsteart1 on 2008-02-27
Iv always used either jfs or xfs because reiser made some interesting comments about the linux kernel, and ext3 just seemed to basic. as for fragmentation, is there a defragmentor for linux, or do the files ystems do that themselves?

---

### Post by bodhi.zazen on 2008-02-27
In my experience the filesystem does not make much, if any difference in performance for the average desktop user. 

Be cautious of "benchmarks" as they are only part of the story.

See this review, although it is a little dated, it reviews some of the options :

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

Also fragmentation is not as much as issue. Yea, every file syestem fragments, but the question is it enough to affect performance ? Linux does not fragment unless your disk is almost full or your are using a lot of torrents.

[http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html](http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html)

	[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by djbsteart1 on 2008-02-28
Thats goos to hear about fragmentation, makes a nice change from ntfs. well, the filesystems will stay as they are when i next do something cretive with a console drunk.

---

### Post by articpenguin on 2008-02-28
The only filesystem i find that can have a problem with fragmentation is JFS.

---

### Post by djbsteart1 on 2008-02-29
hmmmm, ill bear that in mind. are than any tools for defragmentation? or is this done online while using the disk?

---

### Post by articpenguin on 2008-03-01
There is no defragger for JFS. The maintainer says fragmentation can be a problem.

 "When doing a large write, jfs SHOULD at the very least allocate a
contiguous extent large enough for the data being written. Currently it
does not. It allocates on page at a time. So on a fragmented file
system, the file can be quite fragmented. I have plans to improve this,
but I haven't gotten to it yet.

-- 
David Kleikamp
IBM Linux Technology Center"

---

### Post by djbsteart1 on 2008-03-03
Thats both good and bad to hear. I dont do too much with large files thatI plan on keeping so it hopefully wont be a problem. If you need help in testing anything point it to me, always willing to help.

---

### Post by articpenguin on 2008-03-17
my jfs /home is 2% fragmented and it still outperforms a new ext3 parition.

---

### Post by djbsteart1 on 2008-03-22
how do you actual check for the level of fragmentation? I did notice a difference when writing jfs to jfs on the same disk, than writing jfs to ext3 on the same disk. the jfs and ext3 the speed was down to 5mb/s or lower but up at 13mb/s with jfs to jfs. Whither this was the filesystems fault or not i do not know.

---

### Post by articpenguin on 2008-03-22
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

---

### Post by djbsteart1 on 2008-03-23
> **articpenguin said:**
> [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

Jdong is a legend. Great program, I just wish that Linux had something like ZFS, well I guess in a big I'm sure that ZFS-fuse will catch up.

---

### Post by articpenguin on 2008-03-23
just wait a to say 2010. 

[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

[http://oss.oracle.com/projects/btrfs/](http://oss.oracle.com/projects/btrfs/)

---

### Post by djbsteart1 on 2008-03-23
> **articpenguin said:**
> just wait a to say 2010. 

[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

[http://oss.oracle.com/projects/btrfs/](http://oss.oracle.com/projects/btrfs/)

That looks very promising. The fact hta it is already out performing xfs shows signs that this fs good be very good. I wish there were benches with jfs there aswell. I will definatly be watching this.

---

