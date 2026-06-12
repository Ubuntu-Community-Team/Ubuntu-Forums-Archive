---
title: "How does Ubuntu SWAP file work? and can it be installed on a separate drive?"
date: 2007-05-18
forum: General Help
---

### Post by dfarce on 2007-05-18
Hey everyone. I am considering a triple boot system but I am limited to four partitions because of the MBR. Therefore I wouldn't be able to have a common folder on my raid 5 array. Therefore I have a few questions about the Swap partition in Ubuntu. Can it be partitioned on a separate drive than your installation is on? Because then I would use a little 30GB IDE drive I have to put it on. Also, Does Ubuntu use it with the same intensity as the Paging File in windows? If so, then a would a speedier raptor drive be a better idea? My final question is what would happen if I put the swap partition on a separate drive and the drive crashed'? Would I have to reinstall my installation, or is the information volatile and all I would have to do would install another drive and put a partition called SWAP on it?

---

### Post by raja on 2007-05-18
You can get around the limit on number of partitions by using an extended partition.
Still, I dont see any problems in having the swap on a different drive, if you want it that way.
As for the intensity of use, if you have more than a GB of RAM, you rarely will be using swap. And everything in swap would be volatile unless you hibernate the system.
I dont think having a speedier drive for swap is going to make any difference to performance.

---

### Post by dfarce on 2007-05-18
Thanks for the info, so I have 1GB of ram, what would be a good size for SWAP?

---

### Post by FuturePilot on 2007-05-18
I wouldn't go over 2 GB. 2 GB should be more than enough.

---

### Post by seamless on 2007-05-18
> **"FuturePilot"]I wouldn't go over 2 GB. 2 GB should be more than enough.[/QUOTE]According to one of the kernel maintainers (Con Kolivas) that is way to much. His CK patch set FAQ says [URL=&#8221 said:**
> 256MB[/URL] is plenty. Unless you are suspending to disk you do not need that much. If you are suspending to disk then you only need as much swap as you have RAM.

[QUOTE=&#8221;dfarce&#8221;]Can it be partitioned on a separate drive than your installation is on?
Yes.

> **&#8221 said:**
> Also, Does Ubuntu use it with the same intensity as the Paging File in windows?
No. It should never use it unless you run out of RAM.

> **&#8221 said:**
> If so, then a would a speedier raptor drive be a better idea?
No. It will only make a difference if you are using the swap space extensivley but with the amount of RAM you have you should never use it. I have 1GB of RAM in my system and have never used more than 400MB.

> **&#8221 said:**
> My final question is what would happen if I put the swap partition on a separate drive and the drive crashed'?
Not a thing other than you wouldn't be able to write to the swap space if needed. If you were using the space at the time then bad things would happen. However, if your hard drive crashes then other bad things will probably be happening with your hardware making this the least of your worries.

> **&#8221 said:**
> Would I have to reinstall my installation, or is the information volatile and all I would have to do would install another drive and put a partition called SWAP on it?
The only thing you have to do is add the swap partion to the new drive. Then add and entry to /etc/fstab for it to be used. The entry would look like:
```
UUID=THE_UID_FOR_THE_PARTITION none            swap    sw              0       0
```

---

