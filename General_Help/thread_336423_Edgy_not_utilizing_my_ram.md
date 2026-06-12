---
title: "Edgy not utilizing my ram"
date: 2007-01-11
forum: General Help
---

### Post by TheodoreWard on 2007-01-11
I am running Edgy on a Dell D810 laptop with 1gb ram. I have noticed that Ubuntu never seems to use more than about half of the available ram before swapping everything out. I tried opening 3 OS's in vmware today and watched the process monitor and sure enough, my free ram actually got SMALLER and my laptop swapped its @ss off.

here's a picture (which is worth 1000 words) of the process monitor: [http://itd-avenger.osu-okmulgee.edu/~tward/pics/Screenshot-System%20Monitor.png](http://itd-avenger.osu-okmulgee.edu/~tward/pics/Screenshot-System%20Monitor.png)
Any idea what's up with this?

Ted Ward

---

### Post by MontanaMax on 2007-01-11
it sounds like you have plenty of memory - maybe try just turning swapping off

```
sudo swapoff -a
```

More info about swap control is at 

[http://linux.about.com/library/cmd/blcmdl8_swapoff.htm](http://linux.about.com/library/cmd/blcmdl8_swapoff.htm)

If that doesn't work out well, you can turn swap devices back on with

```
sudo swapon -a
```

---

### Post by TheodoreWard on 2007-01-11
Oh, easy enough. Thanks.

---

### Post by bernied on 2007-01-11
There's a lot of information you can get from:
```
cat /proc/meminfo
```
though don't ask me what it all means. It should at least report the correct amount of RAM.

I believe that the kernel uses a lot of 'free' memory as disk cache, but I don't know how or where this is configured. It kind of makes sense if there are files that are accessed more than RAM, to put the files in RAM and the RAM on disk (in swap). This is maybe what is happening when you put your machine under load.

---

### Post by Delkster on 2007-01-11
> **TheodoreWard said:**
> Any idea what's up with this?

The Gnome System Monitor excludes the memory used for disk cache and buffers in the memory usage graph, probably because in most situations the memory allocated for those is practically free as far as the average user is concerned. (It can be freed quickly when needed, and all of it is really just used for improving performance.)

Looks like the kernel thinks that in that particular situation it's worth it to keep the disk cache (or buffers) large even if it means having to swap. That, on the other hand, depends on the disk usage etc.

If you want to see how much RAM is being used for disk cache and buffers, use either the 'free' or 'top' commands in the terminal. The KDE Information Center also shows it all graphically.

---

