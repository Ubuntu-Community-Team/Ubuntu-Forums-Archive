---
title: "Video Joiner?"
date: 2005-09-10
forum: General Help
---

### Post by SmokingGun on 2005-09-10
Anyone know of any video joiner apps?  To join mpegs, avi, divx etc... I've looked all over and can't find a thing.

---

### Post by Radi0ShacK on 2005-09-11
hi,
you can use the cat command, lets say that you have 4 *.mpg files "1.mpg, 2.mpg, 3.mpg and 4.mpg" @ command line type 
```
$ cat 1.mpg 2.mpg 3.mpg 4.mpg >  lol.mpg
``` 
i hope that i ve helped u :)

---

### Post by U5tabil on 2007-02-01
Anyone found a good program to use yet? to merge/join .wma files together or .avi for that mather....

---

### Post by dexter on 2007-02-01
avidemux

---

### Post by hustle7 on 2007-03-04
> **Radi0ShacK said:**
> hi,
you can use the cat command, lets say that you have 4 *.mpg files "1.mpg, 2.mpg, 3.mpg and 4.mpg" @ command line type 
```
$ cat 1.mpg 2.mpg 3.mpg 4.mpg >  lol.mpg
``` 
i hope that i ve helped u :)

Does this work for other formats such as .wmv, .asf, divx, etc.?

---

### Post by atlien on 2007-03-09
Can anyone help me install hjsplit?  I've looked at the readme which says to 
[LIST=1]
[*]Copy HJSplitLX to some location on your harddisk
[*]Start HJSplit for Linux with ./HJSplitLX
[/LIST]
I have the CLX library downloaded and installed (I think) but I still can't get anywhere with it.  I'm trying very hard to learn the command line interface navigation and stuff.  

However, I'm still confused by the directions for installing most programs.  It seems that they are geared towards people who wouldn't need to read them.  And if you do need directions, the ones provided are usually not specific enough to be helpful.  At least for me.

---

### Post by grahams on 2007-03-09
Try avimerge

---

### Post by Mike'sHardLinux on 2007-03-09
I second using avimerge, but I wanted to add that if you want to try it, it is part of the **transcode** package.

---

### Post by Marsolin on 2007-03-10
[Avidemux]("http://linuxappfinder.com/package/avidemux") is very simple to use for this. Open the first file, select Append from the File menu and pick the next file. You can keep going for as many files as you have to join.

---

### Post by atlien on 2007-03-10
I'm getting the feeling that this is maybe a limitation of Ubuntu.  I'm having a difficult time getting hjsplit to work and all of the other suggestions are avi solutions.  

But since I'm not working with avi's....  

Any other thougts?  I have managed to make the cat command work for mpg files.  But that's it for me so far.

---

### Post by Marsolin on 2007-03-10
> **atlien said:**
> I'm getting the feeling that this is maybe a limitation of Ubuntu.  I'm having a difficult time getting hjsplit to work and all of the other suggestions are avi solutions.  

But since I'm not working with avi's....  

Any other thougts?  I have managed to make the cat command work for mpg files.  But that's it for me so far.

Avidemux can handle mpeg and vob files in addition to avi.

---

### Post by atlien on 2007-03-10
Guess I'll be going with that then.  At least until I can find a resource on hjsplit that I can use.  Thanks Marsolin and all who took the time to respond.  

Appreciated!

---

### Post by Tosa on 2007-03-10
I didn't know there was HJ Split for Linux ! I've been using HJ for Win under Wine. It's been working as it should have, but I'm off to install Linux variety...

---

### Post by Tosa on 2007-03-10
Hm, there was some error while installing the required library. HJSplit exits with the error:
[I]./HJSplitLX: symbol lookup error: ./HJSplitLX: undefined symbol: initPAnsiStrings
[/I]But HJSplit 2.3 for Windows works just fine with Wine...

---

### Post by grahams on 2007-03-13
I'm pretty sure avimerge does what you're looking for, if you're just merging avi files. Avidemux can also do this and much more.

sudo apt-get install transcode
avimerge -i file1.avi file2.avi,,, -o mergedfile.avi

example

$ avimerge -i test-000*.avi -o merged.avi 
scanning file test-0000.avi for video/audio parameter
[avilib] V: 29.970 fps, codec=XVID, frames=2094, width=512, height=288
[avilib] A: 48000 Hz, format=0x55, bits=16, channels=2, bitrate=170 kbps,
[avilib]    2912 chunks, 1455264 bytes, VBR
merging multiple AVI-files (concatenating) ...
file 01 test-0000.avi
[test-0000.avi] (000000-002093) (69869.87 <-> 69888.00)
file 02 test-0001.avi
[test-0001.avi] (002094-003399) (113446.78 <-> 113448.00)
file 03 test-0002.avi
[test-0002.avi] (003400-004966) (165732.40 <-> 165744.00)
file 04 test-0003.avi
[test-0003.avi] (004967-006444) (215048.38 <-> 215064.00)
file 05 test-0004.avi
[test-0004.avi] (006445-007926) (264497.83 <-> 264504.00)
file 06 test-0005.avi
[test-0005.avi] (007927-009186) (306539.87 <-> 306552.00)
file 07 test-0006.avi
[test-0006.avi] (009187-010609) (354020.69 <-> 354024.00)
file 08 test-0007.avi
[test-0007.avi] (010610-011048) (368668.67 <-> 368688.00)
... done merging 8 file(s) in merged.avi
[avilib] V: 29.970 fps, codec=XVID, frames=11049, width=512, height=288
[avilib] A: 48000 Hz, format=0x55, bits=16, channels=2, bitrate=170 kbps,
[avilib]    15362 chunks, 8030208 bytes, VBR

---

### Post by Drenhead on 2007-11-08
When I try using AVIDemux to join 2 .avi files, it stops joining when the filesize reaches 1GB.  I looked at the preferences in avidemux and saw one that said do not split large .avi files and I selected it, but it still only gives me a 1 GB file that doesn't have any sound.  How do I get it to go ahead and append the whole file?

---

