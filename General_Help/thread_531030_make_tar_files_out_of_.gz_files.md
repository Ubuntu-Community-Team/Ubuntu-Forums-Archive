---
title: "make tar files out of .gz files"
date: 2007-08-21
forum: General Help
---

### Post by aliyanage on 2007-08-21
Hi all,

Is it possible to make a .tar file out of .gz files?
I have all my .gz files in a directory and would like to free some more space,
so my other question is whether it will help me to turn those .gz files into .tar files?

or is there another solution to free some space? (besides of course deleting them :-D)


Thanks in advance!!!
aliyanage

---

### Post by Aetherius on 2007-08-21
if they are  all .gz files then they are compressed already, sticking them all in another .tar file would not be of much advantage to you.

Sometimes, its down to a simple choice, new hard drive or delete.:lolflag:

You could also do some DVD-archiving.....

---

### Post by aliyanage on 2007-08-21
thanks mate...
will have to find another hard drive in that case :-D

---

### Post by kerry_s on 2007-08-21
> **aliyanage said:**
> Hi all,

Is it possible to make a .tar file out of .gz files?
I have all my .gz files in a directory and would like to free some more space,
so my other question is whether it will help me to turn those .gz files into .tar files?

or is there another solution to free some space? (besides of course deleting them :-D)


Thanks in advance!!!
aliyanage

you could try sticking them all in a folder and tarring it up.
example:
tar cjvf folder.tar.bz2 folder

that's to bunzip it to get it as small as can.

---

### Post by vanadium on 2007-08-21
The normal order in Linux is first to create the tarball then compress the tarball. You would be doing it the other way round, tar the gz archives. I guess that compressing one large file can be slightly more effective than compressing several small files then combining then in one file.

Indeed, tarring is the act of storing several files into one big (archive) file. gzip and bzip are compression tools. Previously, to create a compressed tar archive (tar.gz. tar.bz) one would first run the tar command, then pipe the output through a compression program. Now, the tar command includes the option to do the compression (-z for gzip, -Z for compress, -j for bzip2.

Among the compression tools, bzip would provide most compression, but probably also is the slowest. 'most compression' means: it will shave off a few percentages more than gzip, but the difference is not that significant.

As a final note, with gigabyte USB drives going very cheap now, there is no strong reason to be deleting stuff, except if you do not need it anyway.

---

