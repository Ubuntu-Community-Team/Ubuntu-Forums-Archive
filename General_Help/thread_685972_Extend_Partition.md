---
title: "Extend Partition?"
date: 2008-02-02
forum: General Help
---

### Post by azan00 on 2008-02-02
Hello, I am currently dual booting with windows, and I have a seperate 160GB HD for sharing/storing files. For the most part this hard drive is empty.

However I would like to give my Ubuntu partition more space. So is it possible/logical to extend my ubuntu partition to some unpartitioned space on that 160HD? However I am not sure if I am comfortable with having my main Ubuntu partition be spread across 2 hard drives.

So would it be possible to move my Ubuntu partition completely over to the 160 without damaging anything (and maintaining the dual boot)? How would I do this? But if this isn't possible I will settle with the next best thing, extending the partition.

I am somewhat ignorant when it comes to these things so any insight would be appreciated.

---

### Post by logos34 on 2008-02-02
If I were you I'd [create a separate /home]("http://www.psychocats.net/ubuntu/separatehome") on the 160.  Leave / (root) where it is, but after you copy over the home dir files shrink it down (~7-8 gb should be plenty).

---

