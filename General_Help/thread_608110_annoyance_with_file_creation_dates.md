---
title: "annoyance with file creation dates"
date: 2007-11-09
forum: General Help
---

### Post by mmoalem on 2007-11-09
i find something very annoying and i hope someone has a trick to solve it. i have a dual boot windows xp and ubuntu system with a shared fat32 partition.
the problem i have is to do with file creation dates. 
the problem is when getting photos and movies of my digital camera. when i copy it onto my home partition it keeps the file creation dates. if i copy it directly or from the home partition to the fat32 partition it changes the files dates to the date of copying. if i rotate the images (regardless of partition) it changes the dates of the files. this is a real pain in the neck as i would like my photos and movies to keep the dates they were taken on, windows does it by default as far as i can tell even after jpeg rotation.
i did find a part solution using jalbum i can modify file dates to exif dates but there is no such solution with the mpeg videos as they do now carry such data
please help if you can
cheers
michel

---

### Post by Whiffle on 2007-11-09
[http://linux.die.net/man/1/touch](http://linux.die.net/man/1/touch)

I think that should do it.  Maybe throw it into a bash script and really be cooking with gas.

---

### Post by mmoalem on 2007-11-09
thanks for that but what i was hopeing for was a way of making the default behaviour different rather than applying a second step of remodifying the dates to the original ones.

---

