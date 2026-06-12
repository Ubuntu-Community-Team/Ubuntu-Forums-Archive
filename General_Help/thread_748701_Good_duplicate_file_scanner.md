---
title: "Good duplicate file scanner"
date: 2008-04-07
forum: General Help
---

### Post by bluekage on 2008-04-07
Hey all,
I was browsing around on my computer today when I realized that it could use a good cleaning as far as duplicate images/music/etc. goes. So far I've tried FSLint and KleanSweep, both of which worked great for finding the dupes. However, Im not one to just arbitrarily delete files because a program says its a duplicate of another, I like to check and make sure myself. This is where my problem comes in, Im finding it to be quite the hassle to navigate from directory to directory to validate the scans findings.

So, does anyone know of a good duplicate file scanner, preferably a native app, that allows the user to open the files directly from the program for comparison?

My harddrive, as well as myself, would be very grateful for any recommendations.
Thank you.

---

### Post by bluekage on 2008-04-07
To give a better idea of what I'm looking for, gThumb Image View has a built-in duplicate scanner that temporarily places each group of duplicates into its own little gallery so you can look at them and compare. Only problem is that it doesn't do a very thorough job, it found 2 duplicate groups where as scanning the same directory with FSlint finds 119 duplicate groups.

---

### Post by bodhi.zazen on 2008-04-07
Try fdupes

[http://ubuntuforums.org/showthread.php?p=4400446#post4400456](http://ubuntuforums.org/showthread.php?p=4400446#post4400456)

---

### Post by bluekage on 2008-04-07
Ok, so I've got fdupes now, but how do I use it? Does it have a gui or does it just run through the terminal? Im not too good with the terminal so a little bit of a step by step would be appreciated.

---

### Post by SOULRiDER on 2008-04-07
I made one called twins some time ago:
[http://soulrider.xnet.org](http://soulrider.xnet.org)

Just unpack it somewhere, go to that location and type
```
python Main.py -r -l -v <directory>
```replace <directory> witht he directory you want to scan.

---

### Post by ghostdog74 on 2008-04-07
something simple
```

find /path -type f -exec md5sum {} \; | awk '{
 md5[$1]++
 file[$1]=file[$1]":"$2}
END {
 for ( i in md5 ) {
  if ( md5[i] > 1 ) {
   print i, md5[i],file[i] | "sort -k1"
  }
 }
}' 

```

---

### Post by bluekage on 2008-04-07
SOULRiDER:
I can't seem to get your program to work, I navigated to the Twins folder and typed;

python Main.py -r -l -v /home/bickett/Wallpapers

Which gets this everytime;

Twins version 0.5 - Find duplicate files in your computer.
 USAGE: twins [options] [target directory]
 OPTIONS:
        -s, --slent                 Do not be verbose, only show final report.
        -r, --recursive             Be recursive, enter subdirectories.
        -h, --include-hidden        Scan hidden files, if recursive will scan hidden directories.
        -l, --follow-links          Follow symlinks.
 Author: Mauro de Carvalho

Am I entering the code wrong?

ghostdog74:
I have no idea what it is you want me to do with that bunch of code there. Sorry, I'm not very good with this stuff.

---

### Post by bodhi.zazen on 2008-04-07
> **bluekage said:**
> Ok, so I've got fdupes now, but how do I use it? Does it have a gui or does it just run through the terminal? Im not too good with the terminal so a little bit of a step by step would be appreciated.

fudpes is a command line tool

fdupes <options> <directory>

For example

fudpes -r ~

fdupes -r /home/user/pictures

[http://linux.die.net/man/1/fdupes](http://linux.die.net/man/1/fdupes)

Be careful with the -d option

---

### Post by SOULRiDER on 2008-04-08
> **bluekage said:**
> SOULRiDER:
I can't seem to get your program to work, I navigated to the Twins folder and typed;

python Main.py -r -l -v /home/bickett/Wallpapers

Which gets this everytime;

Twins version 0.5 - Find duplicate files in your computer.
 USAGE: twins [options] [target directory]
 OPTIONS:
        -s, --slent                 Do not be verbose, only show final report.
        -r, --recursive             Be recursive, enter subdirectories.
        -h, --include-hidden        Scan hidden files, if recursive will scan hidden directories.
        -l, --follow-links          Follow symlinks.
 Author: Mauro de Carvalho

Am I entering the code wrong?

ghostdog74:
I have no idea what it is you want me to do with that bunch of code there. Sorry, I'm not very good with this stuff.

It seems I screwed up in my own program... call it without the -v option...

```
python Main.py -r -l /home/bickett/Wallpapers
```

I hope it works. Also, To speed things up it only checks the beginning of the files so you may get some fake-positives. If you want the program to scan the whole file open Main.py and in line 85 change 8*1024 to 0.

Tell me how it goes! (since no one ever needs my program, i wanna know if it has some bugs :P)



bodhi.zazen, youre supposed to promote my program! :mad: :p

---

### Post by ghostdog74 on 2008-04-08
> **bluekage said:**
> 

ghostdog74:
I have no idea what it is you want me to do with that bunch of code there. Sorry, I'm not very good with this stuff.

just save the code as a script and run it through the command line.

---

### Post by Steveway on 2008-04-08
If you want to find duplicate images that aren't the same size or are slightly different (for example one has a watermark on it) then you should take a look at imgSeek.
It can index folders you give to it and sorts them, you can then search for a picture by giving an example-picture or by roughly drawing into a box.

---

