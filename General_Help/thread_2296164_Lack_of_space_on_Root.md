---
title: "Lack of space on Root"
date: 2015-09-23
forum: General Help
---

### Post by Robbyx on 2015-09-23
AMD64

partition size 12g. 
Free 1.2g

I would like to free up space and remove apps I no longer use. I do no know how to start. Is there an app that will help?

---

### Post by grahammechanical on 2015-09-23
Have you tried the Ubuntu Software Centre? That will remove appplications as well as install them.

---

### Post by uninvolved on 2015-09-24
sudo apt-get autoremove will remove unnecessary cruft.

This requires installing more software (you can remove it afterwards if you want) but Ubuntu Tweak has a "janitor" function. BleachBit also cleans up a number of things.

Those may get you started.

---

### Post by Bucky Ball on 2015-09-24
More thorough is:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

You can also shrink the partition next to the / partition and then expand /, if this is possible. If you want to do that, let us know and we can help with that. :)

PS: You can also remove unwanted kernels if you have been using Ubuntu for awhile and you have a heap of them on offer when you boot the machine.

---

### Post by Robbyx on 2015-09-25
> **Bucky Ball said:**
> More thorough is:

You can also shrink the partition next to the / partition and then expand /, if this is possible. If you want to do that, let us know and we can help with that. :)



I assume the way to increase the root partition is to use gparted from  the live CD. Are there any particular risks because root partition is also the boot partition? gparted gives warnings about this. It also warns it can take a very long time to re-arrange the partitions even though it is an SSD. Is it possible to drive image each partition and then to reformat the partitions with increased size and restore the drive images? Is that better than letting gparted re-arrange the partitions?

---

### Post by Bucky Ball on 2015-09-25
Perhaps show us what you have. Open Gparted and take a screenshot. Post it here using 'Adv Reply' instead of 'Quick Reply'> paperclip icon in the toolbar. Cheers.

---

### Post by Robbyx on 2015-09-26
see attached

---

### Post by Bucky Ball on 2015-09-26
Not great. Easiest thing to do would be to boot from Live install media> 'Try Ubuntu'> launch Gparted> shrink sda1 to 2Gb (you don't need an 8Gb /swap) and expand sda2 into the free space.

Goes without saying you should backup any valuable data before commencing.

This may not keep you surviving for long, but long enough.

Looks like you've got a ton of stuff in home but it is small, yet the video and documents folder are set as your data storage and they've got plenty of space. It might be an idea to backup valuable data and rethink your partitioning strategy. An option is to do a regular install, let it create a /home directory, not partition, inside /, delete the default folders it puts in there and create symlinks to your data folders on the other partitions. You could then get rid of the /home partition which is too small for the quantities of data you want to keep there. 

Just a thought. :)

---

### Post by Robbyx on 2015-09-26
Thank you for your useful comments. 

I have been wondering why my home has got so large and I have been deleting old config files no longer needed. I have been carrying forward entries in home  from previous installations of Ubuntu without reinstalling the actual programs. I now have free space of 7.9gb out of a total of 32gb.

The .cache takes up about 6.5gb and included in it is  the .cache for deja-dup. The actual deja-dup backed up files are on a seperate external HD.  Following your comment about sym links can you see any problem with moving it the other drive and then creating a sym link in home/robins/.cache to deja-dup in its new location?

The sym link would free up 4.5gb giving a total of 12.4gb out of 32gb which is probably enough not not to have to do anything else to the home directory. Does that make sense?

---

### Post by Bucky Ball on 2015-09-27
I haven't used deja-dup in awhile, but is there a setting in preferences where can set the target folder (so you can set it to one off your /home or / partition? If so, you could set the partition to where you wish, dump the stuff from the deja-dup folder on /home in there then delete the folder in /home. One possibility.

As I say, haven't used deja-dup in ages, and then only briefly, so not sure of its capabilities. 

If you can move in deja-dup preferences, do so then see what is left in the old /directory (unless it moves the whole thing automatically). Anything worth keeping? The .cache is probably only used as a tool for backing up and contains no valuable data anyway. But I'd double check. :)

---

### Post by Robbyx on 2015-09-29
May I enquire what backup program you use instead of deja-dup? I am not  happy with it but know no better.

---

### Post by Bucky Ball on 2015-09-29
My regular routine is to use Clonezilla, or lately fsarchiver, to clone the / OS partition and Luckybackup (in the repositories) for selected directories.

---

