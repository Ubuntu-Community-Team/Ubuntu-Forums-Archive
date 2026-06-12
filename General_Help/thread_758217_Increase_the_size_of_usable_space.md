---
title: "Increase the size of usable space"
date: 2008-04-17
forum: General Help
---

### Post by Monobi on 2008-04-17
Hi. I ended up installing Ubuntu with Wubi because my CDROM drive was broken. I originally allocated 10 GB for Ubuntu, but I've quickly filled it with various packages. Is there a way to expand the size of the space I can use for Ubuntu? The installation is not on a separate partition.

---

### Post by ago on 2008-04-18
[https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

### Post by Gripp on 2008-04-18
hmm

i couldn't append to fstab
sudo didn't help.  looking at the perms root as a group only has read only access... 
but by this point my system was pretty hosed being that /home/<userName> was no longer present..
couldn't even get on the net any more
so i moved my folder bak from the home.backup to /home
but now i have a disk image in my drive, and i'm not certain what all of those commands did aside from create the image (will deleting it hurt anything?)

and how to write to fstab?

---

### Post by ago on 2008-04-19
> **Gripp said:**
> hmm

i couldn't append to fstab
sudo didn't help.  looking at the perms root as a group only has read only access... 
but by this point my system was pretty hosed being that /home/<userName> was no longer present..

You need to be root to do that, if you boot in rescue mode that should be the case, then you can also append.

> 
couldn't even get on the net any more
so i moved my folder bak from the home.backup to /home
but now i have a disk image in my drive, and i'm not certain what all of those commands did aside from create the image (will deleting it hurt anything?)

The new image is not used if there is no fstab line.
Basically either /home is inside of root.disk, or home sits inside of a home.disk, if there is no explicit line in fstab the first case is assumed.

---

### Post by Gripp on 2008-04-19
yeah, i just used sudo -s to get to root
i thought i had posted that here... guess not :confused:

i think i have that squared away now.  but what if you want to just have a larger root disk?
i'm assuming toporesize or something thereabouts, but want to be sure before i messing up my install

---

### Post by ago on 2008-04-19
That is a similar process as described above, but there are some directories you have to skip (/proc) when copying files. Will do a write up later on. Expanding /home and /usr should be enough though for most purposes

---

### Post by Monobi on 2008-04-22
Yes, I was looking to increase the size of the whole thing, not just the home directory (only a few kb big :) ) . Any reference points for increasing the entire file system size?

---

### Post by airjer on 2008-04-23
> **Monobi said:**
> Yes, I was looking to increase the size of the whole thing, not just the home directory (only a few kb big :) ) . Any reference points for increasing the entire file system size?

I would like to be able to do this also. Is this possible? Soon I'll prolly trash windows completely once I am able to replace everything entirely in Linux, but for now I'd like to increase what I started with.

---

### Post by ago on 2008-04-23
Again, moving /home and /usr to a dedicated partition is a good way to expand your storage space.

---

