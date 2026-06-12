---
title: "Transcode mpeg2enc error"
date: 2005-07-09
forum: General Help
---

### Post by stefanoaguiar on 2005-07-09
Hi there dear Ubuntu fellows.

I've been for 3 hours now searching for this matter, and couldn't get a single clue. Therefore I decided to ask in here.

Let's get to the point.

I have installed transcode swiftly, and all other dependencies for my divx2vcd script. The script can be found in [http://dvdripping-guid.berlios.de/Divx-to-VCD_en.html](http://dvdripping-guid.berlios.de/Divx-to-VCD_en.html)

I used to run this script twice a day, no problem at all, at my old Conectiva 10 installation. Decided to move on completely to Ubuntu and this VCD conversion is the only thing missing. 

This is what I get when running the script: 
```
...
[export_mp2enc.so] (78/4096) cmd=mp2enc -v 0 -r 44100 -b 224 -s -o "/media/dois/vcd/2.processo/1/Pelicula.mpa"
tc_memcpy: using mmxext for memcpy
tc_memcpy: using mmxext for memcpy
Could not create "/media/dois/vcd/2.processo/1/Pelicula.mpa".
**ERROR: [mpeg2enc] Couldn't create output file /media/dois/vcd/2.processo/1/Pelicula.m1v

**** ERROR during transcoding. Code 141

``` I have put only the last lines, to ease things.

Hope someone can help me on that output file.

BTW: I'm running it on a FAT32 drive with all known (by me) permissions allowed.

---

