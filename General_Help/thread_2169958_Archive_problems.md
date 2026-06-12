---
title: "Archive problems"
date: 2013-08-24
forum: General Help
---

### Post by Deety on 2013-08-24
I have several zip archives on an external hard disk which I use for data that I transfer between several machine at several different locations. All 3 of the machines are set to dual boot from W7 or Ubuntu 13.04. On all of the machines I am getting the same problem. All except 2 of the zip files on the archive (external) disk work fine with both operating systems (i.e. I can access the zip files merely by opening them with mouse clicks) The 2 archives which DONT work both show the same rather unhelpful error code which simply says "An error ocurred while loading the archive". The arcives which dont work (In Ubuntu only) are both rather large, one is 14 Gb and the other 28Gb. They contain various video/audio files. The archives which work are between a few Kb and 3Gb. Do I need to install particular archiving software to deal with the larger archives and do I need to treat them differently? All the archives were prepared on windows 7, and as stated earlier they open flawlessly on that system. Sorry about the "newbie" type question, and I hope I've asked on the correct forum!

---

### Post by rai_shu2 on 2013-08-25
Do you have p7zip installed? I think that can handle just about anything.

---

### Post by Kevin_Arnold on 2013-08-25
I realize this isn't a good answer to your question but if you just have audio/video files, why compress them at all. Generally most media files are not going to be compressed much at all so I doubt you gain much space... and you'll have to deal with un-compressing the folder all of the time. If you really need them all in one bundle, you could just tar them without compressing.

---

### Post by rai_shu2 on 2013-08-26
Kevin makes a good point. If your storage starts to get flaky, having big archives will only complicate the issue. What you want are par2 files for each of your videos.

It's a command line program, but it's pretty simple:

```
par2 c -r5 name.par2 list
```

The above creates a new set of parity files (with 5% redundancy).

```
par2 r name.par2
```

The above repairs anything that has gone bad (assuming you have enough parity to cover the damage).

---

