---
title: "Burn to Folder?"
date: 2007-03-08
forum: General Help
---

### Post by gurgle on 2007-03-08
Is there an option in ubuntu or a 3rd party app to burn an entire folder like in OS X? For instance, if I give it a folder about 30 gigs, and ubuntu just burns the folder and asks for a new disk each time? That would be nice. 

Thanks! 

PS - sorry if this is in the wrong place. Maybe we need a "Software" forum?

---

### Post by Jmccaffrey on 2007-03-09
Yes, you want to create a "tarball"(Think RAR file in windows) of the directory, the Tape ARchive(tar) program will process your folder and create one giant ZIP type file out of it.  This way we can easily chop that one file into many parts and reassemble them later.  We will use the split program to chop the files up and the cat program to piece them together again.  In this way we can hold true to the UNIX method of doing things, use many small programs to achieve a larger goal.

Let us assume you have a directory named "My_Music" that is 3GB and your CDs to backup are only 700MB.  We are going to create multiple tar files of the My Music folder so that each tar file is ~700MB in size.

```
tar cj My_Music/ | split -b 700m -d - musicbackup.tar.bz2.
```

What this is doing is creating a compressed tar of the folder, then redirecting that output to the split command. Split will divide the input into 700m files and name them according to the prefix we gave.  In this case musicbackup.tar.bz2.00 musicbackup.tar.bz2.01 etc.. will be created.  Now you can take these files and burn each of them to a CD.

To restore this backup, simply copy all the files to your harddrive again and run this
```
cat muicbackup.tar.bz2.* | tar xjv
```
This will concatenate each archive then process them with the tar command set to eXtract(x argument).  The j means that the input will be compressed with bzip2(hence the bz2 in the file names).

* I am not near my linux computer so I cannot test these commands, however you can read these manuals if I have missed something.
[http://www.die.net/doc/linux/man/man1/split.1.html](http://www.die.net/doc/linux/man/man1/split.1.html)
[http://www.gnu.org/software/tar/manual/tar.html#Multi_002dVolume-Archives](http://www.gnu.org/software/tar/manual/tar.html#Multi_002dVolume-Archives)

---

### Post by gurgle on 2007-03-09
thanks for the reply. I dont think this would work though - if i wanted to listen to any mp3s for instance, then i would need to have each DVD-R handy. This woudlnt really work. I would prefer to just burn them as Data DVD's.

---

