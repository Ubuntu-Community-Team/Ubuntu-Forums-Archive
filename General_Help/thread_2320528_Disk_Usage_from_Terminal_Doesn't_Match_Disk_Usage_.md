---
title: "Disk Usage from Terminal Doesn't Match Disk Usage Analyzer"
date: 2016-04-14
forum: General Help
---

### Post by KenUBF on 2016-04-14
I was looking at the Disk Usage Analyzer in Ubuntu 14.04 and (as you can see from the screenshots uploaded) it's telling me my hard drive is nearly full and that my Home folder is 87.2% full. But when I run the Terminal command 'df -h' I get completely different numbers. It tells me my Home folder is only 4% full. I would imagine that the Terminal output is more accurate, but then again, I could be wrong. Why the discrepancy and which are the correct numbers? Thanks so much!

---

### Post by oldfred on 2016-04-14
Disk usage is percents of total. Or /home is 87%  of the total use of 128GB which is correct.
But df -h also shows total unallocated space and total allocated of 123GB. I expect minor difference of 123 to 128 is differance in what is included.

System hides 5% normally to try to prevent system crash when "full". 
And journal uses some space which then is not user usable. Some include it, others do not. 

And some tools use GiB and others GB.
       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by Impavidus on 2016-04-15
Disk usage analyser lists disk usage of each directory as a percentage of its parent directory. The root directory is its own parent, so it's always at 100%. It does not mention disk usage as a percentage of available space.

---

### Post by ajgreeny on 2016-04-15
> **Impavidus said:**
> Disk usage analyser lists disk usage of each directory as a percentage of its parent directory. The root directory is its own parent, so it's always at 100%. It does not mention disk usage as a percentage of available space.
That catches a lot of people out; it did me many years ago which is why I now find **df -h** so much more sensible and informative, in fact I can't remember if I have used DUA since using 12.04.

---

### Post by mcduck on 2016-04-15
Disk usage analyzer is excellent tool, as long as you use it to find out *where* disk space is used, not how much unused space you have.

...this is pretty much also reflected in being able to scan different directories only, or include mounted devices in the scan etc, useful features but either option wouldn't make any sense for checking used/available space of a specific partition.

Compared to terminal commands, DUA isn't intended as equivalent of *df*, but instead *du*. If you want a GUI equivalent of *df*, just open the System Monitor and you'll see your used/available disk space per partition there.

edit: For example, using *df* (or System Monitor) would easily tell me that I'm using 98% of my storage partition. If wouldn't however, help me figure out what's using the space and where, and what to look at if I need to free some space. DUA (or *du*) on the other hand wold easily tell me how much of the space is taken by my music files, how much is used by Steam games, movies, etc, and possibly reveal that lots of space is being used by video editing application's cache that I've forgotten about (since I never need to interact with the cache directly). Different tools for different purposes. ;)

---

### Post by ajgreeny on 2016-04-15
In order to get more useful info from the du command I have an alias set up ```
alias du=du -h -d 1 | sort -h
``` which sorts the subfolders of any folder in which it's used by size, so by using perhaps a couple of times or more you can drill down through the filesystem and see exactly which folders are using most space.  You could also remove the -d 1 (depth option) and show all folders and subfolders, but that gives you a very long list.

Try it on your home folder and you'll see how useful it can be.

---

### Post by KenUBF on 2016-05-23
Thank you so much for all of the replies. That makes a lot more sense. I use the Terminal now and type  **df -h** to view available disk space and it's much more informative.

---

