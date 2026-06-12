---
title: "Is swap a file system?"
date: 2007-02-13
forum: General Help
---

### Post by FS Lover on 2007-02-13
Is swap itself a file system at all?

---

### Post by elwillow on 2007-02-14
yes it is!
You need to create a dedicated partition for your swap.

There is, maybe, something else out there that I'm not aware of.

so if you are planing to install Linux on a HD, you will need at least 2 partitions:

- The "/" (root of the file system)
- and the swap (usually half your RAM)

you can always create additional partition for your /home, /boot, /tmp, etc....

---

### Post by housam on 2007-02-14
> **elwillow said:**
> yes it is!
You need to create a dedicated partition for your swap.

There is, maybe, something else out there that I'm not aware of.

so if you are planing to install Linux on a HD, you will need at least 2 partitions:

- The "/" (root of the file system)
- and the swap (usually half your RAM)

you can always create additional partition for your /home, /boot, /tmp, etc....



Swap is acting as a virtual memory. and its size usually 2xRAM but not exceeding 1Gb.

---

### Post by Ramses de Norre on 2007-02-14
You can also create a swap file, like windows uses. But the performance of a swap partition is better. And it's kind of a filesystem, in fact every system that takes care of writing data and retrieving it afterwards is a filesystem. It's a pretty primitive filesystem however that mostly writes data sequential to the disk and remembers what's placed where.

---

### Post by FS Lover on 2007-02-14
thanx, can you introduce an official reference that says clearly if swap is a file system or not?

---

### Post by mtice on 2007-02-14
Maybe slightly OT,

> 
Swap is acting as a virtual memory. and its size usually 2xRAM but not exceeding 1Gb.


Gah?  Why not over 1GB?

-Matt

---

### Post by Ramses de Norre on 2007-02-14
Because I've you got more than 512MB ram, more than 1GB of swap would be overkill... Just unneeded space you "throw away", except in some unusual cases it will almost never be used.

---

### Post by ~LoKe on 2007-02-14
1GB of RAM here, and I rarely use more than 100MB of my 500MB swap.

---

### Post by mtice on 2007-02-14
> 
1GB of RAM here, and I rarely use more than 100MB of my 500MB swap.


Interesting, I suppose it has a lot to do with what you're running though right?  As in a heavily loaded mail server will utilize RAM/swap a great deal more than a desktop PC browsing the web.

Matt

---

### Post by FS Lover on 2007-02-17
[http://www.answers.com/main/ntquery?s=file+system&gwp=13](http://www.answers.com/main/ntquery?s=file+system&gwp=13)

-----------

[http://en.wikibooks.org/wiki/Guide_to_Unix/Explanations/Filesystems_and_Swap](http://en.wikibooks.org/wiki/Guide_to_Unix/Explanations/Filesystems_and_Swap)

: ... Some disks are also used for swap, which supplies a temporary storage space for data in memory, when memory is full. Though "swap" resides on a disk, it is not actually a filesystem.
...

---

### Post by mcduck on 2007-02-17
> **housam said:**
> Swap is acting as a virtual memory. and its size usually 2xRAM but not exceeding 1Gb.

If you want to use Hibernate you'll need at least as big swap as your RAM is. But yes, other than that over 1GB of swap is just wasted disk space. (I don't think any of my machines has ever used more than 16MB of swap).

---

### Post by Biochem on 2007-02-26
For all those of you who think more than 1 gig of swap is a wast of HD . Today I ran a image analysis software and consume 2 gig of Ram and 2 gig of SWAP. And probably could have used more.  :-\" 

 But I admit that during normal use I never use any Swap.   \\:D/

---

### Post by bodhi.zazen on 2007-02-26
If you want to calculate how much swap space you need :

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml)

As has been stated, for most users on modern boxes Swap = Ram X 2, max 1 Gb is a good bet ...

Also, there are exceptions hibernation and high use of RAM as stated by Biochem.

Neither of these situations is all too typical (how many have RAM > 1Gb and hibernate for example ... Now I know there are a few, but this is not typical or average).

It seems rare for most average Ubuntu users to use much more then 512 Mb swap, often much less.

---

