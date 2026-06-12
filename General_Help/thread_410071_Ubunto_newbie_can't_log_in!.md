---
title: "Ubunto newbie can't log in!"
date: 2007-04-15
forum: General Help
---

### Post by midlandman on 2007-04-15
OK, I just finished installing Ubunto and did all the updates, but when I restarted it won't let me log in. I get this...
"Gdm could not write to your authorization file. This could mean that you're out of disk space, or the home directory could not be opened for writing. It's not possible to log in, contact the system admin."

The disk was formatted and I allowed more space than what Ubunto recommended in the partitions.
Any ideas about this problem? Thanks.

PS: I did a search and didn't find anything relating to this.

---

### Post by viciouslime on 2007-04-15
Which version of ubuntu are you using? Did you make a separate home partition, or did you just make one large partition for everything?

---

### Post by raja on 2007-04-15
You can try '<Ctr><Alt>F1' to get to a terminal, log in and then see what the status of the /home directory is. ```
ls -l /
```

---

### Post by mac.ryan on 2007-04-15
What version of ubuntu did you installed?
How did you partition your hard drive (file system + size)?
Did you do a normal installation or... ?

Anyhow, you can check if it is a problem of "space" simply booting from your liveCD and launching gparted: even if you don't mount partitions, you can see how much full they are...

---

### Post by midlandman on 2007-04-15
Thanks for the replies...
I may have messed up on the partition, this was the first time I partitioned a HD.
The way I understood what it was telling me, I needed 1 for / and 1 for swap, and I made them both just over 2 G.
As for the version, I think I got the latest, I just DL'd it yesterday (sorry, but I can't recall the version #, I should have wrote it down)
And it was a normal install on a clean HD.

---

### Post by viciouslime on 2007-04-15
The latest is edgy (6.10), but feisty(7.04) will be out on the 19th (4days time! yay! :p) with lots of improvements. You will be able to upgrade from one to the other though.

---

### Post by midlandman on 2007-04-15
That's it, 6.10. When the new version is released, will it just be an upgrade, or will it be a full install where I'll have to format and all that? And will it correct this problem?
And is the partitions I posted previously OK?
I appreciate the help on this.

---

### Post by mac.ryan on 2007-04-15
> **midlandman said:**
> That's it, 6.10. When the new version is released, will it just be an upgrade, or will it be a full install where I'll have to format and all that?

The first case.

> And will it correct this problem?

I don't believe so.

> And is the partitions I posted previously OK?

The partitioning scheme is right, albeit their size can be optimised.

2 Gb as / partition is a bit tight. I would recommend to allocate about 5 Gb (just to stay on the safe side). 2 Gb as swap partition is definitively big, unless you are just working on the rendering of a 1:1 map of the universe ;)
1 Gb should be more than enough, especially if you have 512+ Mb or RAM.

Anyhow I suggest you check how much of your partition is full... so we know for sure if the problem is that one or not... :)

---

### Post by raja on 2007-04-15
> **midlandman said:**
> 
The way I understood what it was telling me, I needed 1 for / and 1 for swap, and I made them both just over 2 G.


You dont need that much for swap. About 1-1.5 times the amount of RAM you have will be a good idea. You can have 4-5 GB for / and preferably have a separate partition for /home.

---

### Post by midlandman on 2007-04-15
> **raja said:**
> You can try '<Ctr><Alt>F1' to get to a terminal, log in and then see what the status of the /home directory is. ```
ls -l /
```

 Ok, so heres a stupid question...where/when do I do this? During start up, before the os starts to boot? Or after I get to the log in page?

---

### Post by raja on 2007-04-15
This will work if your system is booting up and the only problem is with gdm. You should try it at the point where you get the error message. If this does not work, you should boot the system with the live cd as was suggested and then look at the disk space usage with gparted.

---

### Post by midlandman on 2007-04-15
I went a step further and reinstalled it. Now I'm in business. Thanks for all the help.

---

