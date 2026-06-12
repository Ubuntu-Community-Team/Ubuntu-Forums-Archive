---
title: "Is there any way... (I bet there is)"
date: 2008-03-28
forum: General Help
---

### Post by Mazza558 on 2008-03-28
...to remove duplicate filenames (with the same name but a different file format)?

I'm sure there is, but how?

---

### Post by LaRoza on 2008-03-28
The "file" command will give the file types, and it could be used to selectively find files of a certain type.

---

### Post by Mazza558 on 2008-03-28
> **LaRoza said:**
> The "file" command will give the file types, and it could be used to selectively find files of a certain type.

I don't want to delete *all* m4a files, just a few of them - the duplicates of mp3 files.

---

### Post by bonzodog on 2008-03-28
I don't know the exact command, but I suspect that you could use find, then pipe it through rm to remove the m4a files that match mp3's of the same name.

---

### Post by koenn on 2008-03-28
something like this  ? 
```

#!/bin/bash
directory="/home/test"
cd $directory
for FILE in $(ls -1 | grep "m4a" ) ; do
		if [ -e ${FILE%.m4a}.mp3 ] ; then
			rm $directory/${FILE%.m4a}.mp3
		fi
done

```

${FILE%.m4a}.mp3 means : strip m4a from filename, and add mp3
this allows you to test if for a given $FILE.m4a exists a $FILE.mp3, and if so, delete the .mp3 file

make sure it does what you expect
test:
```

## make some diplicate files
 for i in 1 2 3 4 ; do touch file$i.mp3 ; touch file$i.m4a ; done

## make some files without duplicates
for i in  5 6 7 8  ; do touch file$i.m4a; done 

## check
ls

## run script
./ rmDuplicates

## check result
ls

```

I assumed all files are 1 i directory. Doing this across directories is going to be more complicated.

---

### Post by Mazza558 on 2008-03-28
> **koenn said:**
> something like this  ? 
```

#!/bin/bash
directory="/home/test"
cd $directory
for FILE in $(ls -1 | grep "m4a" ) ; do
		if [ -e ${FILE%.m4a}.mp3 ] ; then
			rm ${FILE%.m4a}.mp3
		fi
done

```

${FILE%.m4a}.mp3 means : strip mp3 from filename, and add m4a
this allows you to test if for a given $FILE.m4a exists a $FILE.mp3, and if so, delete the .mp3 file

make sure it does what you expect
test:
```

## make some diplicate files
 for i in 1 2 3 4 ; do touch file$i.mp3 ; touch file$i.m4a ; done

## make some files without duplicates
for i in  5 6 7 8  ; do touch file$i.m4a; done 

## check
ls

## run script
./ rmDuplicates

## check result
ls

```

I assumed all files are 1 i directory. Doing this across directories is going to be more complicated.

Unfortunately, they are in different directories - named by the first letter of the artist and then by album.

---

### Post by koenn on 2008-03-28
do they have extensions that indicate filetype ?

---

### Post by koenn on 2008-03-28
and can you give some examples of "duplicates" with a full path ? Otherwise it's going to be hard to figura out how to mach these duplicates.

---

### Post by Lostincyberspace on 2008-03-28
I have the same problem

Here is a sample of one of the scenarios that I have. I also have some that are much worse.

/home/data/The Proclaimers/Greatest Hits/Im Gonna Be(500 miles)
AND
/home/data/The Proclaimers/Sunshine on Leith/Im Gonna Be(500 miles)

---

### Post by mips on 2008-03-29
I asked this very same question a while back and never really got a satisfactory answer.

I have duplicates all over the show, probably up to 5 of the same file residing in different places. If I could only get rid of the duplicates I will save myself a LOT of HD space.

So if anyone does come up with something that can find files by similair name, size, type etc and has a GUI then it would be great.

---

### Post by beercz on 2008-03-29
Try fdupes

In the repos.

---

### Post by mips on 2008-03-29
> **beercz said:**
> Try fdupes

In the repos.

I googled fdupes and found a usefull wikipedia page listing other similair programs:

[http://en.wikipedia.org/wiki/Fdupes](http://en.wikipedia.org/wiki/Fdupes)
> Similar programs
Other programs that can find duplicates and run under *nix:
**duff**
**dupmerge** - runs on various platforms (Win32/64 with Cygwin, *nix, Linux etc.)
**fdf** - Perl/c based and runs across platforms (Win32, *nix and possibly others)
**freedup *mirror** - POSIX C compliant and runs across platforms (Windows with Cygwin, Linux, AIX, etc)
**fslint**
**liten** - Pure Python deduplication command line tool, and library, using md5 checksums and a novel btye comparison algorithm. (Linux, Mac OS X, *nix, Windows)
**rdfind**
**ua **- Unix/Linux command line tool, designed to work with find (and the like).

---

### Post by koenn on 2008-03-29
> **beercz said:**
> Try fdupes
In the repos.
d*mn, and I just finished a script that finds duplicate filenames across  multiple directories. 
oh well, art for art's sake.

---

### Post by Mazza558 on 2008-03-29
> **mips said:**
> I googled fdupes and found a usefull wikipedia page listing other similair programs:

[http://en.wikipedia.org/wiki/Fdupes](http://en.wikipedia.org/wiki/Fdupes)

Fslint look like the best out of them all. GUI and has a deb available.

---

### Post by mips on 2008-03-29
> **Mazza558 said:**
> Fslint look like the best out of them all. GUI and has a deb available.

Thanks I have not have a look at them yet, will have to see if it is available for arch though :)

---

### Post by beercz on 2008-03-29
> **koenn said:**
> d*mn, and I just finished a script that finds duplicate filenames across  multiple directories. 
oh well, art for art's sake.
Sorry! :redface:

---

### Post by Mazza558 on 2008-04-07
Hmm.. fslint is good, but its duplicate function scans the files themselves... how about duplicate filenames?

---

