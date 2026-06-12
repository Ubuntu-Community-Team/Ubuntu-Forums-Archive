---
title: "external HD with issues. bad sectors/blocks?"
date: 2013-06-27
forum: General Help
---

### Post by nhyrum on 2013-06-27
i have a seagate 320GB external drive. i think it has bad sectors/blocks. it wont load when i plug it into windows, everything locks up(until i unplug it) but loads and runs on ubuntu 12.04 LTS. now my question is... its FULL of music and movies(most of which id like to keep) how can i fix it? copying all the files i REALLY want will take forever... then formatting it... and RE-COPYING the files... doesnt seem very... efficent... any better ideas?

---

### Post by compiledkernel on 2013-06-27
> **nhyrum said:**
> i have a western digital 320GB external drive. i think it has bad sectors/blocks. it wont load when i plug it into windows, everything locks up(until i unplug it) but loads and runs on ubuntu 12.04 LTS. now my question is... its FULL of music and movies(most of which id like to keep) how can i fix it? copying all the files i REALLY want will take forever... then formatting it... and RE-COPYING the files... doesnt seem very... efficent... any better ideas?

DDrescue. 

Watch this video. 

[http://www.youtube.com/watch?v=vqq9A01geeA](http://www.youtube.com/watch?v=vqq9A01geeA)

---

### Post by nhyrum on 2013-06-27
AWESOME!! after i copy the iso, i can farmat the drrive/fix any problems, right?

---

### Post by Ranko Kohime on 2013-06-27
If the drive truly has bad sectors, reformatting will not fix them.  You'll still have the same old problems.  A bad sector is a portion of the disk that has physically gone bad, and can no longer be used.  Generally speaking, hard drives reserve a certain amount of spare sectors above their stated capacity, and use these in the event that a bad sector appears  (because no drive leaves the factory completely free of bad sectors, they all have at least a few).  The drive will not report bad sectors to the S.M.A.R.T. diagnostics until it has consumed that entire reserve, and if that happens, then the drive is on it's way to failure, and data loss.

But as for locking up Windows?  That generally indicates that something could be up with the drive controller, which would be even worse.  If you can copy the data off, do so now.

---

