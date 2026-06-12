---
title: "How long should a duplicate finder take?"
date: 2020-09-29
forum: General Help
---

### Post by mike196 on 2020-09-29
[COLOR=#1A1A1B][FONT=&amp]Hope it's okay to ask this here. I've got a home server running Ubuntu 16.04. I'm planning on updating/upgrading soon and wanted to back up all my media files. I think I did something wrong with rsync and that has led to numerous duplicate files.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I've tried using both rdfind and fdupes and both seems to take a long time. Both programs say there are 1446 files in the directory. I started sudo fdupes -r <dir> over 24 hours ago and it says it's only 41% done (599/1446 files). I wasn't even able to successfully complete an rdfind command; it stuck on the md5 checksum step for multiple hours. This seems like a lot of time. Is this normal for a duplicate find with this amount of files? Is there anything I can do to make it faster?[/FONT][/COLOR]

---

### Post by TheFu on 2020-09-29
It depends on 50 different things and how the tools determine "same-ness."

A few years ago, I wrote a 100% dup-finder. Mine was multi-staged.  
The first stage was to create a list of files sorted by size. If the files weren't the same size, then they weren't duplicates, period.
Next I'd run a CRC check for the first X bytes of the file. No use in checking the entire file if the first 32KB is different.  Some other tools may not be optimized in the same way and might just start by creating md5sum calcs for every file. That can take a very long time.  md5 is known to have some collisions, so perhaps new versions of the tools switched to sha256, which is even heavier on the CPU.

If the storage is slow, that will slow down everything.  USB storage would be slower. Unpowered USB storage is even slower.

If the file names are the same, I'd just make a list of those, sort them, and if the count of a file is more than 1, there is a duplicate. sort+grep can do that.  A quick-n-dirty way to figure out if there are any duplicates would be to get a count of all the source files
**\ls |wc -l**
then do the same on the target directories.  If the number shown isn't the same between the source and the target, you know which has more.

My tool doesn't automatically do stuff, so it isn't useful for others. Plus, mine is recursive. Sorry.

---

### Post by HermanAB on 2020-09-29
I use a program called *hardlink* to find and link duplicates.  It works well enough that I just let it run in a shell until it is done.

---

