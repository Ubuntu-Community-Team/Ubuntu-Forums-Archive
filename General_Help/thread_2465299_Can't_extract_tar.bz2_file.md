---
title: "Can't extract tar.bz2 file"
date: 2021-07-28
forum: General Help
---

### Post by dora5 on 2021-07-28
I made the following efforts to extract libdvdcss-1.4.3.tar.bz2 .   It keeps insisting it isn't a tar. bz2 file.  What in the world else would it be.   How do I extract it?

I really don't get how they could put complete instructions on how to compile without telling us exactly how to extract it!


dora@dora-desktop-ubuntu:~$ tar xf libdvdcss-1.4.3.tar.bz2
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now


dora@dora-desktop-ubuntu:~$ tar -xzf libdvdcss-1.4.3.tar.bz2
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now


dora@dora-desktop-ubuntu:~$ tar -xvjf libdvdcss-1.4.3.tar.bz2
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now
dora@dora-desktop-ubuntu:~$

---

### Post by monkeybrain20122 on 2021-07-29
You didn't tell us where you got that file from. Maybe your download is corrupt. I just tried with download from videolan and tar -xvjf works without problem. Also, you can just right click it and extract. I never remember these -xvjfwxy business.

---

### Post by TheFu on 2021-07-29
x/l/c - extract/list/create
v - verbose
z/j - some sort of compression
f - file ... the next argument that follows is a tar filename of some sort.

Both of these are the same:
```
tar -xjvf somename.tar.bz2
tar xjvf somename.tar.bz
```
Same for 
```
tar -xzvf somename.tar.gz
tar xzvf somename.tgz
```

Tack or without it (dash) don't matter.  This is left over from the sysV or BSD differences in options.

I don't think the extensions matter, since in Unix extensions are for humans. The computer doesn't care.  It will use the "magic number" to determine the type of file.  In user-land, we can use the 'file' command.

```
$ file somename.tar.bz2
```
will show what a file is.
```
$ file The_Linux_Command_Line-William_Shotts.pdf
The_Linux_Command_Line-William_Shotts.pdf: PDF document, version 1.5

```
Simple, handy and correct.

Not that there's anything wrong with getting the source code, but why not just use the APT repo version?
Looks like there are a few packages.  To find the package for your system, use 
```
sudo apt search dvdcs
```
restricted-extras and perhaps libdvdread4 and libdvdread8 are showing in the list returned here.  

**Update**: I used "dvdcs" because it was short, contained enough of the library.  There is a special feel for how many characters to use when searching anything, including google.   
"dvd" would not have been sufficiently specific. Too general.
"libdvdcss-1.4.3" would have been too specific and wouldn't likely find much on different OSes.
Somewhere between those guesses, dvdcs, is easy for human to see, quickly review and decide what is likely the best choice in the results.
Nothing magical about that. Just needs to be part of the package description, somewhere.

---

### Post by dora5 on 2021-07-29
Get ready for it was an html file.  I was supposed to go there to get the actual file.  This in a list of the actual files, mind.

---

### Post by ActionParsnip on 2021-07-29
```

sudo apt install unp
unp libdvdcss-1.4.3.tar.bz2

```

Unp is awesome and extracts all archives with a single command

---

