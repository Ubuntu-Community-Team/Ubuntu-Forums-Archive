---
title: "copying from CD-R, ignoring identical names"
date: 2007-09-03
forum: General Help
---

### Post by lomnick on 2007-09-03
Hi,

I have a large number of CD-Rs containing files (mostly mp3s, but I don't think that's particularly relevant to the problem at hand) organised using a consistent directory structure. I would like to copy these to my hard disk, on a Ubuntu 7.04 system.

For each CD-R, I would like to issue a single command (via command line or GUI, it doesn't matter) and have all the files recursively copied from the CD-R to the hard disk, retaining the directory structure. If a file with the same name already exists in the same directory on the hard disk I would like it to be skipped and for this to be logged.

Ideally, the identical filename situation would *not* be logged if the files were also identical in size (or even better, if they had the same hash). Also in a perfect world, the log would contain not only the names of skipped files, but also their size.

The --update argument to cp is close to what I want, but it is concerned with whether one file is more recent than another and that is not important to me.

Thanks!

---

### Post by lomnick on 2007-11-05
I found the answer to my question elsewhere - rsync is what is needed.

---

