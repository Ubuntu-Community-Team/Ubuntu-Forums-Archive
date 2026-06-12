---
title: "dirsplit exact size for dvd+r"
date: 2017-08-23
forum: General Help
---

### Post by spacemen12 on 2017-08-23
What exact size should I specify for dvd+r when I use dirsplit? I will actually burn many disks, and don't want to realize that the 30th disk is slightly too large and need to start all over again.

---

### Post by TheFu on 2017-08-24
4G or 8G disks?  Not all disks and writers are the same.
**gaffitter -t 4431m** - back when I did stuff like that - at least that is what is in a script.

Something to consider ... 

After doing this for years (I ran the costs almost annually), it became clear that using 4TB HDDs was 
a) cheaper
b) less hassle

rsync is much easier than trying to fit files onto optical media "just write."  A 128G flash drive can replace (15+) 8G DVDs.  A 4TB HDD can replace (500) 8GB DVDs - think of all the time that requires when $120 gets a 4TB HDD these days.  There have been $160 for 8TB disk here the last month.   I think I used 8G DVD-DL for about 2 yrs too long.  Still have about 25 laying around unused.

Of course, sometimes only optical media can be used, so the other options just aren't possible.

---

### Post by spacemen12 on 2017-08-31
Thanks TheFu!

It was also for ~4gb disks.

---

### Post by TheFu on 2017-08-31
My system was to point gafitter at a group of files, run it which created a list of files, chunked into 4G groupings.  I'd redirect that list into a file that would go through a filter making a mv command that put each chunk of files into a separate directory using sequential numbers.  Those numbers became an index.  After burning each to DVD, I'd capture an ls -Rl into a dvd-001.txt file that got placed into a specific directory - for later lookups via egrep.  In the end, there were 3 manual steps.
1) Run the chunking, script-making, file moving stuff
2) Burn the disks, a process that made the dvd-465.txt file (you get the idea)
3) Move the dvd-999.txt file into the special directory (happened to be on a different machine than where the DVD drive was).

Of course, I'd have to do these every few weeks. Swapping and labeling disks with the numbers was a little hassle. Used permanent markers.

I don't have any belief that my size was perfect to the last bit, but it was close enough.  Remember that different drives and different DVDs have slightly different max size limitations.  Burning beyond what the drives doing the reading can see isn't good.  4.4G is about the max.

---

