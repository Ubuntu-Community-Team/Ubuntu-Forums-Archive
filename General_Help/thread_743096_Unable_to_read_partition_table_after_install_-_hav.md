---
title: "Unable to read partition table after install - have used 12hr w/o solution"
date: 2008-04-02
forum: General Help
---

### Post by newhappyxuser on 2008-04-02
Hey everybody! thanks for reading this.I have used now over 12 hour only with this problem reading faqs and how-tos so help would be nice as there are no solution found and many others suffering this kind of problem as well (no, ide_generic_ didnt help)

My problem is confusing me and my friends as some experienced linux users, so maybe there are some point that im missing that you could point :)

Here the facts:

a) machine: K9N neo-v2 mobo, 3GB ram, opteron 1210, 250GB pata (should be compatible)
b) EVERY live-cd works without problems 
c) tried xubuntu 7.10 desktop, xubuntu 7.04 desk, xubuntu 7.10 alternative,  kubuntu 7.04 and hardy heron
c.a) first tried to dualboot vista, then format all, dualboot with xp, format all then only boot with linux so on..
d) tried to install them different "modes" from guided to manual partitioning.
d.a) even gave them "guided control" (in partit.) and same result spawned
e) always same failure(when booting without splash) "unable to read partition table" and few minutes after that goes to busybox "(initramfs)" 


So every time the problem seems to be in partition table. My friend says that I should get known that and make some modifications, in other hand, why ? chkdsk/f resulted with no problems along with WXP and vista so I hope there are different solution.

Im going out now to take some beers to boot my head while waiting your answers [img]http://jumi.lut.fi/~junousia/hymiot/nerd/supernerdplans.gif[/img]

---

### Post by newhappyxuser on 2008-04-02
Actually I lied to you... its now 20hr without any progress with 2hr sleep :lolflag:

---

### Post by newhappyxuser on 2008-04-03
Cmon, somebody have to know something :)

---

### Post by bodhi.zazen on 2008-04-03
Is it a fresh , unformatted, unpartitioned hard drive ? If so , try settig up your partitions with gparted or fdisk prior to installing.

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

If that fails, try installing from the alternate CD.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by newhappyxuser on 2008-04-04
Like I said, I have tried many ways to make the partition, including gparted of course and used the the alt. cd´s too.

---

### Post by newhappyxuser on 2008-04-04
So I assume this is unfixed bug or the motherboard is somehow incompatible ?

---

### Post by newhappyxuser on 2008-04-05
> **newhappyxuser said:**
> So I assume this is unfixed bug or the motherboard is somehow incompatible ?

Yes

---

### Post by Victormd on 2008-04-05
Sorry, just saw this post... were you able to solve it?
I'm not sure I understood your problem. During install your HD is detected but after install, during boot, you get a partition error? Is that it?

---

### Post by newhappyxuser on 2008-04-05
> **Victormd said:**
> Sorry, just saw this post... were you able to solve it?
I'm not sure I understood your problem. During install your HD is detected but after install, during boot, you get a partition error? Is that it?

Indeed. 

I really think that the problem is not in "partition table error" because I have used many programs to partitiate it in right way, like I wrote in the first post.

Bootloader also working correctly, problem initiates after that and goes to busybox..

I assume that you know the "live-cd" version of ubuntu and guided version of partitioning in install-progress.



Yeah, and sorry my bad english :)

---

### Post by louieb on 2008-04-05
Ok boot to a live CD and see if you can post the partition table here. 
To do that:
Open Application>Accessories> Terminal
and run (thats a **lowercase L **at the end)
```
sudo fdisk -l
```
Post the output  here so we can take a look at it and see if anything looks weird or out of place.

---

### Post by Victormd on 2008-04-06
> **newhappyxuser said:**
> Bootloader also working correctly, problem initiates after that and goes to busybox..

I assume that you know the "live-cd" version of ubuntu and guided version of partitioning in install-progress.

Yes, I'm very familiar with it.  I've always preferred the manual install rather than the guided partitioning but I guess you've done that as well...
The only time I've had problems with partitions and ubuntu was when I created them as extended partitions using Windows (very bad idea)... The best I've seen so far is the gparted live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Hope this helps... and if you get a chance, run the command louibe suggested from a live CD and post the results
```
sudo fdisk -l
```

---

