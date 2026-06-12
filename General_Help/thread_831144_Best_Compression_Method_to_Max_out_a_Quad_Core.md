---
title: "Best Compression Method to Max out a Quad Core?"
date: 2008-06-16
forum: General Help
---

### Post by BassKozz on 2008-06-16
I am looking for the best (most efficient) compression method to compress files/directories using 4 threads (maxing out my QuadCore Q6600)?

I've tried [7z]("http://en.wikipedia.org/wiki/7z") but the compression method it uses ([LZMA]("http://en.wikipedia.org/wiki/LZMA")) only uses 2 threads/cores MAX (Ref: [http://www.bugaco.com/7zip/MANUAL/switches/method.htm](http://www.bugaco.com/7zip/MANUAL/switches/method.htm))... So I am looking for something else that will work as efficient (time vs. compression), that will utilize all 4 cores of my processor.  Is there anything out there that can do this?

TIA,
-BassKozz

---

### Post by BassKozz on 2008-06-16
:bump:
Anyone?

---

### Post by sdennie on 2008-06-16
I'm not aware of anything that supports an arbitrary number of threads (but, something might exist).  However, if you are doing your compression from and to the same disk, adding more threads may not speed it up because the bottleneck is likely to be the disk and not the CPU.

---

### Post by BassKozz on 2008-06-16
> **vor said:**
> However, if you are doing your compression from and to the same disk, adding more threads may not speed it up because the bottleneck is likely to be the disk and not the CPU.
Even if using a complex compression algorithm?

---

### Post by sdennie on 2008-06-16
Hmmm.  I may have been wrong.  I just did a bunzip2 on a few large files and it did seem to be CPU bound and not IO bound.

One thing you could do if you are really concerned about compression times would be to write a script that breaks a file into 4 parts and then does something like bzip2 on each of the four parts.  The script would also have to be able to do the reverse.

---

### Post by BassKozz on 2008-06-16
> **vor said:**
> Hmmm.  I may have been wrong.  I just did a bunzip2 on a few large files and it did seem to be CPU bound and not IO bound.
You see, I have 4 cores and 4gigs of ram, I want to use the full potential of my rig to compress files (for backup purposes) to the max...
> **vor said:**
> 
One thing you could do if you are really concerned about compression times would be to write a script that breaks a file into 4 parts and then does something like bzip2 on each of the four parts.  The script would also have to be able to do the reverse.
Probably out-of-my-league...
I am looking for a quick easy (already available) alternative :confused:

---

### Post by wirelessmonkey on 2008-06-16
According to this post.. [http://www.dslreports.com/forum/r19056495-Threaded-bzip2-pbzip2]("http://www.dslreports.com/forum/r19056495-Threaded-bzip2-pbzip2")

... p7zip may be what you want. It scales to number of detected cpus.

---

### Post by BassKozz on 2008-06-17
> **wirelessmonkey said:**
> According to this post.. [http://www.dslreports.com/forum/r19056495-Threaded-bzip2-pbzip2]("http://www.dslreports.com/forum/r19056495-Threaded-bzip2-pbzip2")

... p7zip may be what you want. It scales to number of detected cpus.
I believe p7zip is the same as 7z which is the same as 7za, I ran tests using all three of these from the terminal on a folder containing 1,205 mixed media files totaling 401.3MB, and they all displayed the same results of roughly 2minutes and 57seconds to compress into a .7z file that was only 152.7MB in size, all while only utilizing 2 cores (187% in 'top') and roughly 17.3% of my system memory.

---

For shitz and gigglez I changed the -m0 switch from default (LZMA) to bzip2. and I was able to successfully use all 4 cores (388% CPU usage reported by 'top' for 7z), and only 1.1% of system memory... However the compression took 3minutes and 58seconds (a whole minute longer) and the size of the compressed file was 203.3MB (a whole 50.6MB LARGER) :(

So quad core compression is available just not for the LZMA compression method/algorithm...
So after this discovery, my question has changed, if/when will LZMA support more then 2 cores? And/or is there another compression method/algorithm that is as good as or better then LZMA that will support 4 cores?

---

### Post by BassKozz on 2008-06-17
> **BassKozz said:**
> if/when will LZMA support more then 2 cores?

Found it: [https://sourceforge.net/forum/forum.php?thread_id=2084519&forum_id=45797](https://sourceforge.net/forum/forum.php?thread_id=2084519&forum_id=45797)

---

### Post by veNom_bz on 2008-08-27
> **BassKozz said:**
> I am looking for the best (most efficient) compression method to compress files/directories using 4 threads (maxing out my QuadCore Q6600)?

I've tried [7z]("http://en.wikipedia.org/wiki/7z") but the compression method it uses ([LZMA]("http://en.wikipedia.org/wiki/LZMA")) only uses 2 threads/cores MAX (Ref: [http://www.bugaco.com/7zip/MANUAL/switches/method.htm](http://www.bugaco.com/7zip/MANUAL/switches/method.htm))... So I am looking for something else that will work as efficient (time vs. compression), that will utilize all 4 cores of my processor.  Is there anything out there that can do this?

TIA,
-BassKozz
and an eternity later....

you may want to give pbzip2 a shot. i doubt the compression ratio is as good as lzma but it will be alot faster. 

i am using a core2duo extreme to compress a 450GB tar archive.
with lzma -6 it has taken a day and half so far (it is niced to -20 100% of one core utilized).
with pbzip -9 after running for about 30 mins its file size caught up to that of the lzma archive (not niced 60-98% of three cores utilized).

i will post results of total time and compression when it is finished.

also have you considered spliting your tar into  2 or 4 parts, initializing multiple compression processes and taring the results?

---

### Post by veNom_bz on 2008-09-01
lzma -6 
4 days 3 hours and 16 minutes
input:  500644116480
output: 326054211302
65.2% of original file size.

---

### Post by BassKozz on 2008-09-19
> **veNom_bz said:**
> 
i will post results of total time and compression when it is finished.
Any news on the results?
> **veNom_bz said:**
> 
also have you considered spliting your tar into  2 or 4 parts, initializing multiple compression processes and taring the results?
No I never thought of that... I guess I could go that route.
I'll give it a shot.
Thx

---

### Post by superice on 2010-09-01
7-Zip has a new version of LMZA called LMZA2. You should try it with 4 threads. I tryed  153 mb with 4 threads and ultra compression and it required 2221 mb of ram so it should use the full potential of your rig. I only have 2 GB of ram so it didn't finish :). I use 3 threads. LMZA and 7z is the highest compression you can get, according to a few tests.

---

