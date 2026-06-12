---
title: "Find Command - Sort Order - Changing Files to Sort AlphaNumerically"
date: 2019-03-29
forum: General Help
---

### Post by Alan5127 on 2019-03-29
Hi All,

I have a media player that shows directories / files out of (alphanumerical) order that are stored on a flash drive.

I had a' flash' (sorry!) of inspiration, and wondered if the order it shows them is the same as the order that 'find' lists the files in Linux, so I tested by running:

```
find .
```

from the main directory on the flash drive, and it gave the files in the same order as the media player.

Now, I can sort the output of find by piping through sort (say):

```
find . | sort -z
```

but that doesn't help fix the sorting on the media player.

At first I thought it might be sorting by the date / time modified, so I did this:

```
touch -t 201901010100 *
```

which seemed to help, but did not entirely fix it, and in particular, some of the directories are still out of order.


For reference, the sort order is also the same as:

```
ls -U
```


Searching around, I found these discussions of the same thing, but I cannot see how to use that knowledge to solve my problem:

[URL="https://serverfault.com/questions/181787/find-command-default-sorting-order"]https://serverfault.com/questions/181787/find-command-default-sorting-order

[/URL][https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u](https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u)

[ https://stackoverflow.com/questions/9582059/find-command-listing-results-in-directory-order]("http://https://stackoverflow.com/questions/9582059/find-command-listing-results-in-directory-order")



Question:

How can I change the directories and files, so that they are output, by default, from 'find', alphanumerically?


If it is not possible to change the existing directories / files, would it perhaps be possible to write a bash script that does it?
I am thinking something that does this:

0) Start with /flashdrive/ and move all the existing directories / files into a directory on my PC
1) Run find through sort on the directory / subs
2) copy the items returned by find | sort, one by one, from my hard drive to the flashdrive

This would therefore 'rebuild' the file structure by creating new files on the flashdrive.

Step 0 can be done manually, but steps 1 and 2 would be tedious to do manually, so would need to be automated.



Any suggestions welcome!

Thanks,

Alan.

---

### Post by Holger_Gehrke on 2019-03-29
Both your Player and find show the files in the order they were written. Copying or moving the files somewhere else and then writing them back in the order you want is the only way to get this right. You don't need to use find|sort for this; wildcards in the bash (*?[...]) expand to an alphabetically sorted list of files matching the pattern you give. So something like 'mv /media/MyUserName/VolumelabelOfPlayer/* ~/AnEmptyDirectory; cp -R ~/AnEmptyDirectory/* /media/MyUserName/VolumelabelOfPlayer' should basically be enough.

Holger

---

### Post by Alan5127 on 2019-03-29
Hi Holger,

> **Holger_Gehrke said:**
> Both your Player and find show the files in the order they were written. Copying or moving the files somewhere else and then writing them back in the order you want is the only way to get this right. You don't need to use find|sort for this; wildcards in the bash (*?[...]) expand to an alphabetically sorted list of files matching the pattern you give. So something like 'mv /media/MyUserName/VolumelabelOfPlayer/* ~/AnEmptyDirectory; cp -R ~/AnEmptyDirectory/* /media/MyUserName/VolumelabelOfPlayer' should basically be enough.

Holger

Thanks for that - I should have realised myself :-)

I am wondering if a simple move (mv) would be suffient?

Something like:

```
mv /media/MyUserName/VolumelabelOfPlayer/AllFiles1/* /media/MyUserName/VolumelabelOfPlayer/AllFiles2/
```

or is the intermediate copy required so that the directories and filesare all created anew (I assume they are not with the above, since it is almost instantaneous)?


I can test later when I get the drive, but just wondering.

Thanks,

Alan.

---

### Post by Alan5127 on 2019-03-29
Hi Holger,

I realised this could take some time, since it involves moving all the files from the flash drive to my hard drive, then copying them all back.

The main issue is actually with the sub-directories, rather than the files within those sub-directories (or, if I could solve that issue at least, it would be a great win).

Therefore, I figured I could perhaps just re-create the directory structure, and then move the files into the new structure, which means I am moving the bulk of the actual data (files) from one location to another on the same drive, which should be fast.


To do this, I ran a directory listing, copied into a text file, and prepended each line with a mkdir to get a bash script that looks like this (run from inside the original folder structure - hence using 0_NewStructure so that it is easy to find):

```

#!/bin/bash

mkdir -p "0_NewStructure/A"
mkdir -p "0_NewStructure/A/A01"
mkdir -p "0_NewStructure/A/A02"
mkdir -p "0_NewStructure/A/A03"
mkdir -p "0_NewStructure/B"
mkdir -p "0_NewStructure/C"
mkdir -p "0_NewStructure/C/C01"
mkdir -p "0_NewStructure/C/C02"
mkdir -p "0_NewStructure/D"
mkdir -p "0_NewStructure/D/D01"
mkdir -p "0_NewStructure/D/D01"
mkdir -p "0_NewStructure/D/D02"
mkdir -p "0_NewStructure/D/D03"
mkdir -p "0_NewStructure/D/D04"
mkdir -p "0_NewStructure/D/D05"


```

Those aren't the real directory names of course, just an easy to follow example.

I ran that script, and all works fine, except....

If I then do a:

```
cd 0_NewStructure && find . -type d
```

I get:

```

.
./C
./C/C01
./C/C02
./A
./A/A01
./A/A02
./A/A03
./B
./D
./D/D01
./D/D01
./D/D02
./D/D03
./D/D04
./D/D05

```

For some reason, one (only one, but that may be random) directory ('C' in the above example) is still out of order, despite explicitly creating each directory, one at a time, in the right order.


I am really confused!

Alan.


Edit:  I actually already knew this from the link above (unimpressive memory!):

[URL="https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u"]https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u


[/URL]

---

### Post by Holger_Gehrke on 2019-03-30
If your player is using FAT as its filesystem, fatsort from the repositories should help you clearing things up. Take a look at it's manual page [here]("https://www.mankier.com/1/fatsort").

Holger

---

### Post by Alan5127 on 2019-03-30
Hi Holger,

I just checked, and it looks like the filesystem is NTFS.

I had a look around, but could not find an obvious equivalent to fatsort for NTFS?

Thanks,

Alan.

---

### Post by Impavidus on 2019-03-30
I don't know the details, but I did a small experiment and it seems the order of directory entries is pretty random.
```
$ mkdir test
$ cd test
$ ls -aU .
.  ..
$ touch ../f1
$ touch f2
$ ls -aU .
.  ..  f2
$ touch f3
$ ls -aU .
.  ..  f2  f3
$ ln ../f1
$ ls -aU .
.  ..  f2  f1  f3
$ touch ../f4
$ touch f5
$ ls -aU .
.  ..  f2  f1  f3  f5
$ touch ../f6
$ mv ../f4 .
$ ls -aU .
.  ..  f2  f1  f3  f4  f5
$ mv ../f6 .
$ ls -aU .
.  ..  f6  f2  f1  f3  f4  f5
$ touch f7
$ ls -aU .
.  ..  f6  f2  f1  f3  f4  f7  f5
```Note that some files were created in the test directory, others were moved there or hardlinked. This is on an ext4 filesystem.

---

### Post by him610 on 2019-03-30
> How can I change the directories and files, so that they are output, by default, from 'find', alphanumerically?
Well, if you don't mind a little manual command line work... this is what I do to order a list of mp3 files for into a ordered playlist that goes onto a custom CD.
Directory list: 2burn, 2burn-1, 2burn-2,....
File listing:
```

~/Music/2burn-1$ ls
'01 - Tiny Dancer (Remastered).mp3'
'02 - Earth, Wind & Fire - September.mp3'
'03 - Heart Of Gold.mp3'
'04 - Heaven.mp3'
'06 - Why Me.mp3'
'07 - Every Breath You Take (Remastered 2003).mp3'
'08 - Keep on Loving You.mp3'
'09 - Wonderful Tonight.mp3'
'10 - Peter Frampton - Baby, I Love Your Way.mp3'
'11 - Lee Ann Womack - I Hope You Dance.mp3'
'12 - Kansas - Dust in the Wind.mp3'
'13 - Neil Diamond - Red Red Wine.mp3'
'14 - Pink Floyd - Another Brick in the Wall, Pt. 2.mp3'
'15 - I Want To Know What Love Is (2008 Remastered Version).mp3'
'16 - Everybody Hurts.ogg'
"17 - Blue Ain't Your Color.ogg"
'18 - Sister Golden Hair.ogg'

```

---

### Post by Alan5127 on 2019-03-30
Hi Him 610,

> **him610 said:**
> Well, if you don't mind a little manual command line work... this is what I do to order a list of mp3 files for into a ordered playlist that goes onto a custom CD.
Directory list: 2burn, 2burn-1, 2burn-2,....
File listing:
```

~/Music/2burn-1$ ls
'01 - Tiny Dancer (Remastered).mp3'
'02 - Earth, Wind & Fire - September.mp3'
'03 - Heart Of Gold.mp3'
'04 - Heaven.mp3'
'06 - Why Me.mp3'
'07 - Every Breath You Take (Remastered 2003).mp3'
'08 - Keep on Loving You.mp3'
'09 - Wonderful Tonight.mp3'
'10 - Peter Frampton - Baby, I Love Your Way.mp3'
'11 - Lee Ann Womack - I Hope You Dance.mp3'
'12 - Kansas - Dust in the Wind.mp3'
'13 - Neil Diamond - Red Red Wine.mp3'
'14 - Pink Floyd - Another Brick in the Wall, Pt. 2.mp3'
'15 - I Want To Know What Love Is (2008 Remastered Version).mp3'
'16 - Everybody Hurts.ogg'
"17 - Blue Ain't Your Color.ogg"
'18 - Sister Golden Hair.ogg'

```


Apologies if I missed something, but what command line tools did you use to get it to sort alphanumerically by default (without using, say, 'sort' or other)?

As per above, 'find' does not (necessarily) return them so - it *might*, but no certainty.  If easier, 'ls -U' returns the same output as 'find', wheras 'ls' defaults to getting the list, then sorting it, then returning it to you (so it should always return alphanumerical listings).


Thanks,

Alan.

.

---

### Post by him610 on 2019-03-30
Actually, it can be done from your favorite file manager also.
I actually put the numbers into each file name - very low tech. Like I said, it is a little manual work. There may be a better, more automated way to do this, but I only do it once every few months.
From the command line....
```
mv 'El Paso.mp3'  '01 - El Paso.mp3' 
```
Mind placement of the single quotes.

---

### Post by Alan5127 on 2019-03-30
Hi Him610,

> **him610 said:**
> Actually, it can be done from your favorite file manager also.
I actually put the numbers into each file name - very low tech. Like I said, it is a little manual work. There may be a better, more automated way to do this, but I only do it once every few months.
From the command line....
```
mv 'El Paso.mp3'  '01 - El Paso.mp3' 
```
Mind placement of the single quotes.

I can rename the files, but the issue is that 'find' does not return them alphanumerically, and therefore they sort out of alphanumerical order on the media player.

Maybe re-read my original post :-)

Thanks though!

Alan.

---

### Post by Impavidus on 2019-03-31
I've been digging a bit and found the following.

If your flash drive uses a fat32 or fat16 filesystem, the tool fatsort is made precisely for this purpose.```
sudo apt install fatsort
```and read the manual.

If your flash drive uses a more modern filesystem, you can't put the files in just whatever order you want using whatever filename you want:
[https://superuser.com/questions/373611/how-to-physically-reorder-files-03-mp3-01-mp3-02-mp3-ls-f-in-a-direct](https://superuser.com/questions/373611/how-to-physically-reorder-files-03-mp3-01-mp3-02-mp3-ls-f-in-a-direct)
[http://ext2.sourceforge.net/2005-ols/paper-html/node3.html](http://ext2.sourceforge.net/2005-ols/paper-html/node3.html)
[https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u](https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u)

To make lookup of directory entries faster, they are stored in a specific data structure, where they can be retrieved (on ext4 systems) ordered by the hash value of the name. This hash makes the order pretty much random, but every pair of names will always come in the same order on any particular filesystem. For example, on one partition I get```
$ ls -f
.  ..  0000x02  0000x05  0000x06  0000x01  0000x03  0000x04  0000x07
```but on another partition I get```
$ ls -f
..  0000x04  0000x03  0000x07  .  0000x06  0000x01  0000x02  0000x05
```All files were created in numerical order.

If you don't mind some random characters as a suffix or prefix to your filenames, you can still sort them in whatever way you want, but it may take some trial and error:```
$ls -f
.  ..  2289x01  2355x02  3784x03  2571x04  0000x05  5629x06  0000x07
```

---

### Post by Alan5127 on 2019-03-31
Hi Impavidus,

> **Impavidus said:**
> I've been digging a bit and found the following.

If your flash drive uses a fat32 or fat16 filesystem, the tool fatsort is made precisely for this purpose.```
sudo apt install fatsort
```and read the manual.


Unfortunately not - as per above, it is NTFS.


> **Impavidus said:**
> 

If your flash drive uses a more modern filesystem, you can't put the files in just whatever order you want using whatever filename you want:
[https://superuser.com/questions/373611/how-to-physically-reorder-files-03-mp3-01-mp3-02-mp3-ls-f-in-a-direct](https://superuser.com/questions/373611/how-to-physically-reorder-files-03-mp3-01-mp3-02-mp3-ls-f-in-a-direct)
[http://ext2.sourceforge.net/2005-ols/paper-html/node3.html](http://ext2.sourceforge.net/2005-ols/paper-html/node3.html)
[URL="https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u"]https://unix.stackexchange.com/questions/13451/what-is-the-directory-order-of-files-in-a-directory-used-by-ls-u
[/URL]

Yes - basically the same references as per my OP.


> **Impavidus said:**
> 

To make lookup of directory entries faster, they are stored in a specific data structure, where they can be retrieved (on ext4 systems) ordered by the hash value of the name. This hash makes the order pretty much random, but every pair of names will always come in the same order on any particular filesystem. For example, on one partition I get```
$ ls -f
.  ..  0000x02  0000x05  0000x06  0000x01  0000x03  0000x04  0000x07
```but on another partition I get```
$ ls -f
..  0000x04  0000x03  0000x07  .  0000x06  0000x01  0000x02  0000x05
```All files were created in numerical order.

If you don't mind some random characters as a suffix or prefix to your filenames, you can still sort them in whatever way you want, but it may take some trial and error:```
$ls -f
.  ..  2289x01  2355x02  3784x03  2571x04  0000x05  5629x06  0000x07
```


I had actually tried playing around like that, and it might be viable for a few files, but with, say, fifty or a hundred files (sub-directories) the chances of getting a result randomly is very small, and any time I added a new file, it would be thrown out again.


So, do you think it is not possible to achieve what I want to do?

Thanks,

Alan,

---

### Post by ajgreeny on 2019-03-31
Another thought that may be relevant is to use an audio tag editor which I found the easiest way to make sure album files I had ripped by various means from CDs played in the proper order, important if, for example, you've ripped a CD of classical symphonies or concerti.

There are several packages in the repos to do this and I think some media player packages have this as an available facility.

---

### Post by The Cog on 2019-03-31
I just made this little ditty that will copy the contents of one folder to another, in sorted order.
I don't know if NTFS keeps files in directory order. 
Copy the following to a file called sortedcopy.py. 
Edit the SRC and DST directory names near the top of the file to refer to your source and destination folders. 
Run it with the command **python sortedcopy.py**
If you have any doubts about its safety, get someone else to review the code before you use it. You shouldn't blindly trust stuff you see in the internet.
```
#!/usr/bin/python

# Perform a directory content copy, sorted in track order

SRC = "/home/myname/usb-copy"
DST = "/media/myname/player"

import os, sys, re, shutil

def vsort(strings):
    kvpairs = []
    for s in strings:
        chunks = re.findall(r'\d+|\D+', s)
        key = [int(chunk) if chunk.isdigit() else chunk for chunk in chunks]
        kvpairs.append([key, s])
    return [kv[1] for kv in sorted(kvpairs)]

def copydir(src, dst):
    slen = len(src) + 1
    for root, subs, files in os.walk(src):
        for sub in vsort(subs):
            dstdir = "%s/%s/%s" % (dst, root[slen:], sub)
            print dstdir
            os.mkdir(dstdir)
        for fname in vsort(files):
            sf = "%s/%s" % (root, fname)
            df = "%s/%s/%s" % (dst, root[slen:], fname)
            print df
            shutil.copy(sf, df)

copydir(SRC, DST)

```

---

### Post by Alan5127 on 2019-03-31
Hi The Cog,

> **The Cog said:**
> I just made this little ditty that will copy the contents of one folder to another, in sorted order.
I don't know if NTFS keeps files in directory order. 
Copy the following to a file called sortedcopy.py. 
Edit the SRC and DST directory names near the top of the file to refer to your source and destination folders. 
Run it with the command **python sortedcopy.py**
If you have any doubts about its safety, get someone else to review the code before you use it. You shouldn't blindly trust stuff you see in the internet.
```
#!/usr/bin/python

# Perform a directory content copy, sorted in track order

SRC = "/home/myname/usb-copy"
DST = "/media/myname/player"

import os, sys, re, shutil

def vsort(strings):
    kvpairs = []
    for s in strings:
        chunks = re.findall(r'\d+|\D+', s)
        key = [int(chunk) if chunk.isdigit() else chunk for chunk in chunks]
        kvpairs.append([key, s])
    return [kv[1] for kv in sorted(kvpairs)]

def copydir(src, dst):
    slen = len(src) + 1
    for root, subs, files in os.walk(src):
        for sub in vsort(subs):
            dstdir = "%s/%s/%s" % (dst, root[slen:], sub)
            print dstdir
            os.mkdir(dstdir)
        for fname in vsort(files):
            sf = "%s/%s" % (root, fname)
            df = "%s/%s/%s" % (dst, root[slen:], fname)
            print df
            shutil.copy(sf, df)

copydir(SRC, DST)

```

Wow - I am very much indebted to you for writing that for me.

I will have to wait until I get home to try it on the drive, but I did do something similar above with the mkdir script I posted.

Does your Pythpn script do something that is different in substance to what I tried?  I have not (yet) gotten to grips with Python (my next ToDo!), so highly likely I might be missing what it does exactly.

Thanks,

Alan.

---

### Post by Alan5127 on 2019-03-31
Hi ajgreeny,

> **ajgreeny said:**
> Another thought that may be relevant is to use an audio tag editor which I found the easiest way to make sure album files I had ripped by various means from CDs played in the proper order, important if, for example, you've ripped a CD of classical symphonies or concerti.

There are several packages in the repos to do this and I think some media player packages have this as an available facility.


Not sure how that would work / help?

The media player consistently displays the directories / files in the same order that 'find' / 'ls -U' both do - tags on the files would not come into it (unfortunately).

Thanks,

Alan.

---

### Post by The Cog on 2019-04-01
> **Alan5127 said:**
> Does your Pythpn script do something that is different in substance to what I tried? 
Nothing really different. It just copies everything from one folder to the other. But it does it in order. 

I resorted to python instead of bash script for 2 reasons (after spending time with bash): 
Firstly the sort. It treats numbers as numbers not text: "Track 9 - blah blah" will sort earlier than "Track 11 = blah blah". You don't have to put leading zeros on the front.
Secondly, I had real trouble with quotes and spaces in filenames when using bash. I never got the quoting right when trying combine find, sort and cp. Some sed-fu would have done it eventually, I suppose.

Of course it only helps if NTFS keeps the order they were copied into it. But it seems form earlier posts that it does. Hope it works for you.

---

### Post by Alan5127 on 2019-04-01
Hi The Cog,

> **The Cog said:**
> Nothing really different. It just copies everything from one folder to the other. But it does it in order. 

I resorted to python instead of bash script for 2 reasons (after spending time with bash): 
Firstly the sort. It treats numbers as numbers not text: "Track 9 - blah blah" will sort earlier than "Track 11 = blah blah". You don't have to put leading zeros on the front.
Secondly, I had real trouble with quotes and spaces in filenames when using bash. I never got the quoting right when trying combine find, sort and cp. Some sed-fu would have done it eventually, I suppose.

Of course it only helps if NTFS keeps the order they were copied into it. But it seems form earlier posts that it does. Hope it works for you.

Thanks again.

Sadly, it appears that NTFS does not have a directory order that is related to the creation time of files - a file created later can 'directory sort' prior to one created earlier.

Darn!


Alan.

---

### Post by The Cog on 2019-04-01
That's a shame. Maybe you can use FAT32 instead? Unless you have files bigger than 2G, that is.

---

### Post by Alan5127 on 2019-04-01
Hi The Cog,

> **The Cog said:**
> That's a shame. Maybe you can use FAT32 instead? Unless you have files bigger than 2G, that is.

Yeah - the same drive has music, but also videos that the kids watch in the car, and they are frequently over 2GB.

I guess I could transcode (?) them to a lower resolution than the original, but not really keen on getting into that each time!

Thanks,

Alan.

---

