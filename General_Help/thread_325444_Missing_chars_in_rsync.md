---
title: "Missing chars in rsync"
date: 2006-12-25
forum: General Help
---

### Post by random_mike on 2006-12-25
Hi, I use Rsync to sync my files between my Linux, Windows and Mac computers. It works fine except for one thing. When i sync files from my Windows computer with files that have chars like "åäö" the filenames gets all messed up in Windows.

For Windows i use cwRsync 2.0.10.

Same problem:
[http://www.linuxquestions.org/questions/showthread.php?t=465567](http://www.linuxquestions.org/questions/showthread.php?t=465567)

I also have a samba server running and when i copy files from there it is ok. The filenames stay the same.

Any ideas? ](*,)

---

### Post by random_mike on 2006-12-26
Same problem:
[http://www.ubuntuforums.org/showthread.php?t=155795&highlight=%E5%E4%F6](http://www.ubuntuforums.org/showthread.php?t=155795&highlight=%E5%E4%F6)

Still looking for a solution. It has something to do with differnt char encodings.
In Linux i use UTF-8 and windows uses god knows what, i think ISO-8859-1.
Trying to change in Windows is impossible.

I found a conversion tool for Mac and Linux, Convmv.

So when I've synced my Linux computer with my Windows one in the direction 
Windows -> Linux.
I have all the files etc but filenames that include "åäö" look very strange in Linux.

But in Linux i can fix that with the tool Convmv. for example:
convmv --notest -f ISO-8859-1 -t UTF-8 -r *

And it converts all the strange chars to swedish ones, and everyting is good.

But when i now run rsync in the direction Linux -> Windows all "åäö" look strange in Windows.

Does anyone know a simlar tool like Convmv for Windows?

If so i could just convert useing the tools before i rsync

---

