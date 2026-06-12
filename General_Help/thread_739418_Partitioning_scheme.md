---
title: "Partitioning scheme"
date: 2008-03-29
forum: General Help
---

### Post by defmomo on 2008-03-29
Hey, I just bought a 500GB hard drive, and was gonna reformat my PC and start all over again. I am planning a new partitioning scheme and here is what  i have come up with so far, with what i read from this forum and other sites:
```

/dev/sda        /* Current hard drive, 160GB */

-Partition 1
/swap ==>   2GB

-Partition 2
---Extensible Partition
/boot  ==>    500MB
/         ==>    20GB
/usr    ==>    40GB
/var    ==>    5GB
/tmp    ==>    5GB
/home ==>    (Rest of Space)

```
*************************
```

/dev/sdb            /*   New 500GB hard drive     */

-Partition 1
/swap     ==>  2GB

-Partition 2
---Extensible Partition
/data      ==>   (Rest of Space)

```

Is this efficient since i will be using it mostly for audio/video storing and manipulation, a little server work, and some development, and also trying out new distros from time to time.
I also have a few questions:
1. Is having the swap at the begining of the drive boost speed?
2. Does having multiple swaps and giving them similar priorities really result in speed increase?
3. does the /boot really need to be on a primary partition?
4. Is an extended partition slower than a primary one?

I'll take any suggestions you might have that would help make this more efficient

---

### Post by stefangr1 on 2008-03-29
1. It depends a little, when you have a modern computer with a lot of RAM I think putting it behind your root directory is the best.
2. It's faster if you have multiple hdd's.
3. Yes.
4. No.

I don't think its necessary to have /boot   /   /usr  /var and  /tmp on different partitions. 
500mb is very large for /boot anyway (50mb should be enough).
I also think that a total of 70gb for the sum of  /boot   /   /usr  /var and  /tmp  is really unnecessary. I think, since you have /home on a separate partition, 20gb should already be enough.

---

### Post by defmomo on 2008-03-29
I need the /var and /boot in different partitions because /var will contain my web server, and /boot different kernel images for different distros and i need it accessible from different distros.
/tmp will be my temporary directory for extracting archives for example, and i will need it separate for security reasons.
As for /usr, i'll leave it in the / partition as you suggested.

---

### Post by defmomo on 2008-03-29
Can i get any more sugestions?

---

