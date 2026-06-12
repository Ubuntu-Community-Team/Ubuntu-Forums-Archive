---
title: "Heavy disk usage locks me up (disk trashing without swap)"
date: 2007-11-25
forum: General Help
---

### Post by kung fu buntu on 2007-11-25
Every couple of days I'm haunted by sporadic heavy disk usage that basically locks me up and forces me to reboot. I can't do anything... not even moving my cursor.

Today the force was strong with me  :lol: and I was able to reach top before I got completly out of the system. There I noticed 3 things:
1) I only had about 15MB free (in a 2GB system)
2) I noticed kswapd0 was using 1%-5% of the CPU (kswapd0 may not be the culprit but I suspect it)
3) after 30-60 seconds (this time it was fast so I didn't had to reboot) the system got OK and I had 160MB free memory

I don't have a swap file so I suspect kswapd0 it clearing unneeded memory pages... I just don't get it why it... works this way...  :x 

Any ideas on how can I fix this?

Thanks!

---

### Post by scrooge_74 on 2007-11-25
You should have a swap file, also you should remove those packages you downloaded that are just taking space

sudo apt-get autoremove

clear old logs in /var/log

---

### Post by rune0077 on 2007-11-25
If its possible, try running the System Monitor to see what is taking up all those resources.

Are you running AWN? I've noticed that sometimes the python application used by the stacks plugin takes up 100% of one of my processors and I have to kill the application (somekind of weird bug or just my system that's screwed up, dunno).

---

### Post by kung fu buntu on 2007-11-26
> **scrooge_74 said:**
> You should have a swap file, also you should remove those packages you downloaded that are just taking space
sudo apt-get autoremove
clear old logs in /var/log
I don't need a swap, I have 2GB of RAM. The kernel should free old pages instead of writing to swap or  trashing to disk...
And what do clearing the system for free HDD space has to do with it? :confused:

> **rune0077 said:**
> If its possible, try running the System Monitor to see what is taking up all those resources.
Are you running AWN? I've noticed that sometimes the python application used by the stacks plugin takes up 100% of one of my processors and I have to kill the application (somekind of weird bug or just my system that's screwed up, dunno).
According to **top -b -n 1 | less** I should have about 1GB free RAM. Xorg eats about 400MB, then other apps like opera, iceweasel and java eat a couple more.
The thing is that the kernel doesn't free old pagefiles when it should. It waits for the last moment and then starts trashing...

---

### Post by scrooge_74 on 2007-11-26
Sorry mate, try another kernel, maybe is a bug in your current one?

---

### Post by Monkey77 on 2007-11-26
The kernels memory management is based around the fact you have a swap partition (although technically you don't have to have one), windows is just the same.  No matter what size RAM you have you should always have a swap partition.

The system will use any RAM that applications do not use for a system cache, to help with response times.  

System monitor should give a good indication of what is causing the slow down, perhaps an indexing service is needing more RAM.  When memory is not used in a while it is pushed out to the drive rather than running a more complex algorithm to determine if the memory should be freed.  Without a swap partition you are forcing the memory manager to be aggressive more often than is needed.

Regards
Phil Hannent

---

### Post by kung fu buntu on 2007-11-26
That doesn't justify the heavy I/O.
There's no swap... there should be no I/O.

Do you have any suggestions for the monitor tool I should use?


Off course there is also the possibility this has nothing to do with RAM or swap, and it's just some messed up daemon that is doing something it shouldn't.

---

### Post by Monkey77 on 2007-11-26
I would expect there to be I/O as after it has done a scavenge of the memory it has got to get the runtime files that it originally needed, therefore getting the application from the disk again.

As an example of what might be happening, your application might want 100MB of RAM for drawing windows positions and loading data.  It asks the kernel for the space.  The kernel gets all aggressive, clears the space, then the application can work away getting the data but it needs to also reload the libraries and executables at the same time.

A more authoritative answer would come from a kernel virtual memory hacker:
[http://lkml.org/lkml/2007/9/24/491](http://lkml.org/lkml/2007/9/24/491)

However as you say it might not be kswapd.  Also just for completeness which version are you running?

Phil Hannent

---

### Post by bingoUV on 2007-11-26
to determine who is using your disk, read [http://ubuntuforums.org/showpost.php?p=3806273&postcount=17](http://ubuntuforums.org/showpost.php?p=3806273&postcount=17)

The above post is not long, and helps to quite effectively determine the disk abuser.

---

