---
title: "Altering partitions from an ubuntu live cd"
date: 2008-02-02
forum: General Help
---

### Post by reumar on 2008-02-02
Is it possible to resize or delete partitions on a hard disk using an ubuntu live CD?
If it is, how?
Thanks

---

### Post by Nexusx6 on 2008-02-02
Maybe, but its better to use a partioning program right off of your computer rather than off a CD. 

I recommend using gParted:

```
sudo apt-get install gparted
```

After you get it, gparted is ran from the terminal with sudo, like this:

> sudo gparted

---

### Post by njparton on 2008-02-02
There's a gparted live cd available from sourceforge that you can boot from.  I found gparted from the live cd to be very unstable - not something you'd want to risk!

---

### Post by reumar on 2008-02-02
I'm trying to remove the linux partition from a windows machine that was dual boot until fairly recently, when I used SuperGrubDisk to restore the machine to solely loading windows - don't get me wrong, I have enjoyed using linux so far, but as I'm not the only user of the machine in the house I shouldn't have installed it on there in the first place. Which is why I can't use a linux install on the hard drive to resize/delete partitions.

---

