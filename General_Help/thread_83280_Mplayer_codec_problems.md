---
title: "Mplayer codec problems"
date: 2005-10-28
forum: General Help
---

### Post by speedsix on 2005-10-28
Hi, I'm running Breezy x86 with Mpplayer. I have download the Win32 codec package as per the Restricted Formats page but I get an error re. cannot find vo codec when playing certain wmv videos? I'm sure I can play some wmv9 files but I have a few that I only get sound on.

The mplayer site has 2 binary codec packages,

**Essential codecs** - Which I presume is the same as the Win32 package listed in the Restricted Formats doc although it seems to have a few more files?

**All codecs** - What does this have not in the win32 pack? I have tried adding the files to the directory mplayers lists (somewhere in /usr/.. can't remeber) But no joy.


Thanks

Dom

---

### Post by taurus on 2005-10-28
I would grab the all version and after unpacking it, you have to move everything in it to /usr/lib/win32/

---

### Post by speedsix on 2005-10-28
I'll give that a go thanks.

I'm wondering if mplayer is trying to use ffmpeg codecs first, maybe I need to specify -afm acm,dshow to force mplayer to use win32 codec family first.

Will try later

Dom.

---

### Post by speedsix on 2005-10-28
Nope, tried the -vfm flag, must be a duff wmv file. Nevermind.

---

