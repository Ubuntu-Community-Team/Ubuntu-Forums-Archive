---
title: "partitions for multiple distros"
date: 2013-06-08
forum: General Help
---

### Post by DJWYMAN on 2013-06-08
Ok I finally after many years of playing with linux but always having a dual or triple booting machine and used either windows or osx as my main OS and just played with linux distros for fun and curiosity got rid of windows on my current machine and only have Ubuntu 13.04 as the only thing installed.  I set up a swap partition, a / partition, and a /home partition so if I want to do a clean install I will not have to do anything with my personal files.  To add to this I left 25gb free to put another distro if I so choose.  This is were my question comes in...will the second distro use the same /home partition and swap or will I have to make more swap?  

If the I cannot or should not use the same /home partition I will not worry about making a second one as the second distro will basicly be just for playing around with and be revolving door so to speak.  On that front though is there a safe way to use the same files for multiple distros?  For instance lets say I am using ubuntu and lubuntu...can I use the same music, video, documents, and so on folders?  If so how?


On a side note I am EXITED that I have finally cut the cord from windows completly. :D

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by DJWYMAN on 2013-06-09
well I will never hibernate a distro to boot up another so that being said being able to not have to have more than one swap would be preferable for me.  On the /home partition the main reason I made it was when say 13.10 comes out instead of having to throw my personal files on a removable drive or something I can just replace the / partition and install the new distro.  sharing the /home was not a big deal for a second distro as like I say it will mostly just for trying other distros more than anything.  and it is highly unlikely I would keep them or use them for any real task like using said files.  I was more curious about that being possible more than any thing.

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by Megaptera on 2013-06-09
Something here that may be helpful: " A lazy way to increase multi-booting in Linux" from ...
[http://forums.pcper.com/showthread.php?401513-A-lazy-way-to-increase-multi-booting-in-Linux](http://forums.pcper.com/showthread.php?401513-A-lazy-way-to-increase-multi-booting-in-Linux)

---

### Post by mikodo on 2013-06-09
^^
One should not use their same /home folder with different installs, especially across different distros because the .dot files in home may not be compatible with each other.

Newer wisdom suggest setting up data (disk/partitions). See the first link below by Carla Schroder, explaining why to do this and how she explains setting up the data (disk/partition) and  the second by oldfred in the link to a Ubuntu forum thread where he details how to symlink the data from the /mnt/data (folders) to your /root installs ( in post #4 ).


[http://www.linuxtoday.com/blog/2009/08/painless-linux.html](http://www.linuxtoday.com/blog/2009/08/painless-linux.html)


[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)


You will have to make the /Backup/folder on the other disk first without the config files. Include the folders you need. Like, Music, Documents, Pictures, Videos, etc. Then they will be accessible in each /root install on /mount/Data after the symbolic links, described by oldfred are completed.

  Basically, what ahallubuntu is telling you, with links on how to do it. ( Something you might find useful ).

---

