---
title: "HDD, partitions and fragmentation"
date: 2007-10-11
forum: General Help
---

### Post by Trance Gemini on 2007-10-11
hi!

While I was installing Gutsy as my second os on my laptop, one thought came to my mind.

I have a laptop with windows xp on it. I have been using it for long time. Some weeks ago I decided to install a second OS on it (Gutsy). So I downloaded Acronis Disc Director suite and made about 8gb of free space at the end of my hdd.

The question is: does Acronis make this free space absolutely free? It's just it had free it up rather quickly, and I doubt it could move all the data, from thouse last 8gb of my hdd somewhere outside this area.

Could it be that the physicaly the data that was in that 8gb space remain there, and MFT has a new record of that it has 8gb free, but physicaly this 8gb space is located not as a continous sectors at the end of my hdd, but are spread over the entire hdd (as a fragmented file).

Please read my [post]("http://ubuntuforums.org/showthread.php?t=573029"). You can see there I mentioned, that I have a lot of hrrrrrrr sounds - it prety much reminds me when I have a very fragmented  data and work under windows.

Maybe there's a way to see the sectors under linus as they are usualy shown under some defragmentation program under windows (will squares of different colors that show is the sector free, used, locked, etc.)

Thanks

---

### Post by zvacet on 2007-10-11
First defragment win patition few times.After that use Gparted

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

and resize your partition.In free space install Ubuntu.

---

### Post by Trance Gemini on 2007-10-11
I have already installed ubuntu, so this will help me only if I reinstall it.

---

### Post by dabl on 2007-10-11
Look for strigi-daemon -- you can kill the process and/or remove the package.  It can be a monopolizer of your resources.  :)

---

