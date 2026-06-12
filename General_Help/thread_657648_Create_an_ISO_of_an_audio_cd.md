---
title: "Create an ISO of an audio cd"
date: 2008-01-03
forum: General Help
---

### Post by lsutiger on 2008-01-03
I am trying to create an image of an audio cd.
when I run:
dd if=/dev/cdrom0 of=file.iso
I get ```
dd: opening `/dev/cdrom0': No such file or directory

```

What gives?

---

### Post by AlexThomson_NZ on 2008-01-03
Shouldn't that be:

dd if=/dev/cdrom of=file.iso

---

### Post by yabbadabbadont on 2008-01-03
I doubt that it will work anyway.  Audio CDs do not have a normal filesystem on them that can be dumped to a file.  Your best bet is to use something like abcde to create a single flac (lossless audio) file with embedded cue sheet.  This can be played directly, or later used to recreate the original CD.

---

### Post by Kzin on 2008-01-03
> **yabbadabbadont said:**
> I doubt that it will work anyway.  Audio CDs do not have a normal filesystem on them that can be dumped to a file.  Your best bet is to use something like abcde to create a single flac (lossless audio) file with embedded cue sheet.  This can be played directly, or later used to recreate the original CD.

This guy speaks the truth.

---

### Post by lsutiger on 2008-01-03
FYI: I get this error```
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00869629 seconds, 0.0 kB/s

```
with dd if=/dev/cdrom of=file.iso
I will try the abcde...I have it and used it a few times, but what would be the command forwhat I am trying to do?

In addition, all I am trying to do is create an image so I can do multiple copies. It's a cd that I mixed on my tables a couple of years ago and have some requests for more. I can do it in windows quite easily, but I rather not. :)
On a learning curve here

---

### Post by yabbadabbadont on 2008-01-03
> **lsutiger said:**
> I will try the abcde...I have it and used it a few times, but what would be the command forwhat I am trying to do?

```
man abcde
```

;)

(That's what I would have to do in order to answer your question, so you might as well read it yourself.  :D)

---

### Post by lsutiger on 2008-01-03
heh! Ok I was trying to be lazy...thanx for setting me straight!

But now that I have a huge flac file, how do I burn that to a cd? Isn't the flac gonna be larger than 700 MBs?

---

### Post by yabbadabbadont on 2008-01-03
```
man abcde
```
:lol:

No, the flac file will be smaller than the CD otherwise, what would be the point?  ;)

Flac is a lossless, compressed format.  (use the "--best" option for maximum compression)

Edit: Even though I have all my CDs ripped, I'm currently reinstalling abcde to see if I can help you.  (am I great or what?  :D)

---

### Post by yabbadabbadont on 2008-01-03
Oakily Doakily, here is the relevant portion of the abcde man page:
```
       -1     Encode  the  whole  CD in a single file. The resulting file uses the CD title for tagging. If the resulting format is a flac file
              with an embedded cuesheet, the file can be used as a source for creating other formats. Use  "-1  -o  flac  -a  default,cue"  for
              obtaining such a file.

```

So you would configure abcde using your ~/.abcde.conf file to set all the usual things.  Where to store the output, temporary directories, default options, ...  Then you would use ```
abcde -1 -o flac -a default,cue
``` to produce the flac file.  I'll have to look at the actual abcde script to see if it embeds the cue sheet into the file as a tag or just creates one in the output directory with the flac file.  I think you would then just have to load the cue sheet into k3b (or similar) in order to recreate the original audio CD.  Again, I'll have to dig through the script to see what it is doing to be sure.

---

### Post by logos34 on 2008-01-03
Here's what you want:

> abcde -1 -M -o flac

(rips entire CD to single flac file with embedded cue sheet)

EDIT: it appears you already did that

then:

abcde -d [singlefile].flac	-->extracts individual flac files from above

abcde -d [singlefile].flac -o ogg	-->extracts individual flac files from single file and converts to ogg

There a way to make a copy using  **cdrdao** command with read-toc and read-cd options

man cdrdao:
> 
read-toc
              Analyze each track of the inserted CD and create a toc-file that
              can be used to make a more or less exact copy of the  CD....

---

### Post by yabbadabbadont on 2008-01-03
I've done some further reading on this and it appears that the CUE sheet that is stored in the flac is incomplete.  It is fine for seeking and extracting the individual tracks, but it cannot be directly used to create a new CD.

Edit: Hmm.  That information may have been outdated.  In the test I ran, the embedded cue sheet looked complete to me.  I didn't feel like trying to burn a CD to test it though.

---

### Post by lsutiger on 2008-01-06
cdrdao copy
thats it!

---

### Post by Kzin on 2008-02-09
Woah, this help file has step by step instructions on how to create an iso of an audio CD.... I've never heard of it!!!!!!
[https://help.ubuntu.com/community/CreateIsoFromCDorDVD](https://help.ubuntu.com/community/CreateIsoFromCDorDVD)

Just stumbled across it and thought of this thread

:guitar:

HTH

---

### Post by lsutiger on 2008-02-09
HAHA! Thanx Kzin! That was quite simple, but probably not well know. I searched the forum for the answer and didn't ind anything. I will have to keep the help sight in mind.

Good news, bad news:
It created an ISO. CD\DVD creator in Gnome can not open it. :(

---

### Post by andrew.46 on 2008-05-12
Hi,

As has been mentioned cdrdao is what you are after. Have a look at:

[http://www.andrews-corner.org/burning.html#audio](http://www.andrews-corner.org/burning.html#audio)

for a few starting ideas.

         Andrew

---

