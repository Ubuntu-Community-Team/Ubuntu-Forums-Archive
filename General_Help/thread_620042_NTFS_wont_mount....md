---
title: "NTFS wont mount..."
date: 2007-11-22
forum: General Help
---

### Post by blop on 2007-11-22
HI all, i have read a bunch of posts and done some head scrathing myself....but im afraid im going to have to post.


I had a NTFS volume which up until last night worked fine....now however it wont mount. It appears in GPARTED and in fstab with the correct path....

/dev/sdb1 /media/sdb1/ ntfs-3g defaults,locale=en_US.utf8 0 0

but it is not mounted in the correct directory...if i unmount it with GPARTED and then remount it...and navigate to the folder /media/sdb1 its empty...

any help appreciated!!

---

### Post by sumanta on 2007-11-22
I experienced the similar kind of stuff. Actually, I have found that the interface between NTFS and Ubuntu some times not working. I solved it by formatting the volume using a windows machine to FAT32. Now it works fine for me.

---

### Post by blop on 2007-11-22
Is FAT32 support in Ubuntu/Linux better than with NTFS?

I though all issues were solved with NTFS and it was me being a monkey!

---

### Post by kpkeerthi on 2007-11-22
Can you change
> /dev/sdb1 /media/sdb1/ ntfs-3g defaults,locale=en_US.utf8 0 0
to 
> /dev/sdb1 /media/sdb1/ ntfs-3g defaults 0 0
and see if it helps, although it 'should' work with the former. May be it helps.

---

### Post by kpkeerthi on 2007-11-22
There are several reasons why you may not want to use FAT32:
1. Its a dated filesystem and slow
2. It does not support files larger than 4 GB. (You may not need large file support but that depends on how you use it)

You may consider formatting that volume to ext3. Windows (but not Vista) can read/write to  ext3 using [this ]("http://www.fs-driver.org/index.html")driver.

---

### Post by blop on 2007-11-22
HI, thanks for the replies...

the fstab edit has made no difference after a reboot. i may format the partition as ext3 drive.....

I have been having so many issues with Ubuntu of late...its untrue....gutsy was a disaster for me so i retreated to my working Feisty image and now my drives have dropped. I got away from windows due to all the maintenance issues that came with it....its a shame to see Ubuntu becoming a problem to.

---

