---
title: "Brasero .bin .toc files"
date: 2008-04-28
forum: General Help
---

### Post by cold_fu5ion on 2008-04-28
Hi,

I have just upgraded (clean install) to 8.04 and went to make a copy of an audio cd using Brasero. It produces a .bin and a .toc file, how can I mount these to access their content without burning to a cd? 

I have come across many, many posts on how to mount .iso files and I have even tried to install cdemu but I can't for the life of me work that one out as this have changed since 7.10 it seems.

I any ideas on how to get to the data without burning to a cd?

Thanks.

---

### Post by justleen on 2008-04-28
you can install the package bin2iso to convert the image.. and you might want to check the preferences of brasero, i think..

---

### Post by vanadium on 2008-04-28
Audio CDs do not have a file system and therefore cannot be mounted into your file system.

On a sidenote: I hope that brassero is using cdparanoia for copying an audio CD. Otherwise the copy might be unreliable.

---

### Post by cold_fu5ion on 2008-04-28
Hi, 

Thanks for the replies. I just tried a similar app to bin2iso called 'bchunk' but it failed, I think because there is no .cue file created, only a .toc. [http://ubuntuforums.org/showthread.php?t=93706&page=2](http://ubuntuforums.org/showthread.php?t=93706&page=2)

As for audio cds not being mountable, I have in the past (windows) created an iso of an audio cd using dvd-decryptor, mounted it with dameon tools, and ripped the audio tracks.

I think I will have to resort to burning some cds, and as far as I can see you can't change the preferences of what time of file brasero outputs (The properties box is grayed out).

[edit] I sure hope the copy is reliable as I sent the original CD to the UK this afternoon![/edit]

---

### Post by troynall on 2012-10-25
> **cold_fu5ion said:**
> Hi, 

Thanks for the replies. I just tried a similar app to bin2iso called 'bchunk' but it failed, I think because there is no .cue file created, only a .toc. [http://ubuntuforums.org/showthread.php?t=93706&page=2](http://ubuntuforums.org/showthread.php?t=93706&page=2)



this will create your CUE file -

toc2cue yourfile.toc yourfile.cue

I know this thread is KINDOF old but I thought I would answer this problem.

also


[LIST]
[*]Install cdrdao and bchunk: sudo apt-get install cdrdao bchunk



[*]
[*]Assume your .toc/.bin files are yourfile.toc and yourfile.bin, run the following commands:
[LIST]
[*]toc2cue yourfile.toc yourfile.cue



[*]bchunk yourfile.bin yourfile.cue yourfile.iso



[/LIST]
[/LIST]

---

### Post by oliwek on 2012-12-25
Thanks for your input, troynall, it helped at least someone here ):P

---

### Post by oldos2er on 2012-12-25
Old thread closed.

---

