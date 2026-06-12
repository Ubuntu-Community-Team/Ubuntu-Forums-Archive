---
title: "Why does Linux cache file copies?"
date: 2007-07-01
forum: General Help
---

### Post by obrouni on 2007-07-01
Hi,

Quick question. Why does Linux cache large file copies? For example if I say copy a ISO file from one drive to another it tries to store the entire file in cache. I can understand this for smaller files since you might need to access them in the near future. But I find it very annoying that after copying large files all the previous contents of the cache (Firefox, evolution, terminal) have been flushed out to make way for the large files, meaning they take longer to load up.

Is there any special command to copy/read a file without caching it?

Not a major problem, just a slight moan. Any ideas?

Nick

---

### Post by PaulFr on 2007-07-01
Sorry Nick, I did not understand your problem - AFAIK, the Firefox cache is in your home directory ( for example, my present Firefox session has the cache files in ~/.mozilla/firefox/czqsdsd6.default/Cache ). When I copy a file from one disk to disk, I do not see any files missing in my Firefox cache (enter **about:cache** in the Firefox address box to see details about the Firefox cache). I do not know about the other applications, however. What command are you using to copy such large files ?

---

### Post by tillo on 2007-07-01
I guess he's talking about [mmap()]("http://en.wikipedia.org/wiki/Mmap"), but I don't have an answer.

---

### Post by obrouni on 2007-07-02
Not sure if mmap() is it. This looks a bit more like it:-

[http://en.wikipedia.org/wiki/Page_cache](http://en.wikipedia.org/wiki/Page_cache)

Basically is there a way to tell Linux not to cache files over a certain size when opening/copying? So that you don't lose all the useful things stored in the cache.

Nick

---

### Post by ddaedalus on 2007-07-02
He means the System cache. He wants to say that Firefox is been swapped out during such operations. Basically he wants Linux to be less aggressive in swapping out unneeded data.
What you need is "swappiness".
```

echo "0" > /proc/sys/vm/swappiness

```
This snippet makes the Kernel swap only when its absolutely needed. The default value for Ubuntu is 66 ( of 100 ). There is nothing in Linux you can't change ;)

---

### Post by Enverex on 2007-07-02
> **ddaedalus said:**
> He means the System cache. He wants to say that Firefox is been swapped out during such operations. Basically he wants Linux to be less aggressive in swapping out unneeded data.
What you need is "swappiness".
```

echo "0" > /proc/sys/vm/swappiness

```
This snippet makes the Kernel swap only when its absolutely needed. The default value for Ubuntu is 66 ( of 100 ). There is nothing in Linux you can't change ;)

He doesn't mention SWAP at any point.

What he's asking is exactly what he asked. Is there any way to copy a file without caching it. What you suggested wont help in the slightest because it's not swapping in the first place. When a file is copied it gets rid of old data in RAM (RAM, not SWAP) to cache what was just copied instead, meaning say, Firefox or whatever that was still cached in RAM (still RAM, not SWAP) has been flushed now, so that when he next goes to use it it takes as long as a cold start would take for it to open. So he wants to know how to copy a file without the system caching it in RAM.

---

### Post by obrouni on 2007-07-02
Exactlly. Thats exactlly what I mean. I have 2GB of ram and very rarely, if ever, get any swapping. Its the flushing of the cache during large file copies, which then impacts loading programs from cold that I want to avoid.

---

### Post by PaulFr on 2007-07-03
I've spent some time researching this and one command that can help seems to be **dd**. Here's a (unscientific ?) test I ran (comments welcome):```
sync
sync
sync
cat /proc/meminfo > /tmp/meminfo_before
cp 1_GB_file 1_GB_file.backup
cat /proc/meminfo > /tmp/meminfo_after
sync
sync
sync
cat /proc/meminfo > /tmp/meminfodd_before; 
dd iflag=direct,nonblock if=b_1_GB_file bs=64k oflag=direct,nonblock of=b_1_GB_file.backup
cat /proc/meminfo > /tmp/meminfodd_after
sdiff /tmp/meminfo_*
sdiff /tmp/meminfodd_*

```Note the iflag and oflag values. For my system, the difference in the Cached: entry is huge for **cp** but much smaller for **dd**. I verified with md5sum that the files were identical for both commands, and the time taken was approximately equal. Does this help ?

---

### Post by tillo on 2007-07-03
@PaulFR: You probably found the solution, my compliments.

@obrouni: Virtual Memory, Page Cache, mmap... are all approximately the same thing. Just read the article you post about, sometimes :)

---

### Post by PaulFr on 2007-07-03
I was waiting to repeat the test in the Recovery Console without the distraction of X / GNOME and other processes. Here are my numbers in the Recovery Console:```

cp:
MemTotal:      2066556 kB                                       MemTotal:      2066556 kB
MemFree:         53260 kB                                     | MemFree:       1907692 kB
Buffers:          5076 kB                                     | Buffers:          7484 kB
Cached:        1964608 kB                                     | Cached:         125140 kB
SwapCached:          0 kB                                       SwapCached:          0 kB

dd:
MemTotal:      2066556 kB                                       MemTotal:      2066556 kB
MemFree:         51972 kB                                     | MemFree:         51752 kB
Buffers:          7416 kB                                     | Buffers:          5164 kB
Cached:        1964556 kB                                     | Cached:        1966936 kB
SwapCached:          0 kB                                       SwapCached:          0 kB
```
Nick, hope this helps.

---

### Post by obrouni on 2007-07-03
Excellent, thank you. just what I was looking for.

One quick last question. Is there anyway to do this with other things? IE I have just watched a large AVI, which has also filled my cache.

I know this sounds really silly thing to be picking up on but its annoying when most of the time Ubuntu is so snappy and responsive (much more than windows) but as soon as I copy, open or extract a large file, I click terminal, firefox or gedit and its slow. Really takes away from the experience.

I think more app's need to take something like this into account:-
[http://insights.oetiker.ch/linux/fadvise.html](http://insights.oetiker.ch/linux/fadvise.html)

Or can I achieve the same by preloading my post common applications using preload?

---

