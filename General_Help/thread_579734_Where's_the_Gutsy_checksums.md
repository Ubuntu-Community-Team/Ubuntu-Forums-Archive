---
title: "Where's the Gutsy checksums??????"
date: 2007-10-18
forum: General Help
---

### Post by olavjunior on 2007-10-18
Got many errors when trying to install with alternate cd. Checksum mismatches all the way!

I've done a checksum of the cd, but can't find the checksums for gutys on ubuntu.com :(

---

### Post by por100pre1 on 2007-10-18
Read [this]("http://ubuntuforums.org/showthread.php?t=579716").

---

### Post by olavjunior on 2007-10-18
Thanx!
But now I'm really confused! Cause the checksum for the alternate cd matches mine. But when I tried to install, it said every file was corrupt cause checksum mismatch :S

What shall I do?

---

### Post by por100pre1 on 2007-10-18
Weird, try burning at 4x or close speed. Try another burning program just to be sure.

---

### Post by olavjunior on 2007-10-18
ok, I used nautilus at lowest speed. Hm, having a hard time believing that the burn was corrupt, but I'll give it a go! I'll have to use my mates windows-machine 8-[

---

### Post by olavjunior on 2007-10-18
The checksum document in  the cd is last modified the 16.okt. I downloaded it after the ubuntu.com announced the release from their official sites. Does this mean that the final release actually was finished the 16.?

---

### Post by FredB on 2007-10-18
> **olavjunior said:**
> The checksum document in  the cd is last modified the 16.okt. I downloaded it after the ubuntu.com announced the release from their official sites. Does this mean that the final release actually was finished the 16.?

Yes. I'm using Gutsy since beta, and starting from 16 october, no more updates were available...

---

### Post by olavjunior on 2007-10-18
Well, I've been using the beta as well, so I know there's not been any updates. But I wanted a fresh install to see if some bugs could be resolved.

I tried burning the cd again. The cheksums are ok. But when I do a test of the cd from the installation menu, I get errors. The cd is corrupt it says. Tried installing anyway, but I get errors installing the main system, and errors when I try to install apps.. Got the grub fixed, so I can boot into windows at least. 

I'm kinda frustrated! Anybody else had problems with the alternate cd?

---

### Post by maybeway36 on 2007-10-18
Try:
```
md5sum -b /dev/cdrom
```

---

### Post by olavjunior on 2007-10-19
I couldn't do that since I was running from live-cd. But I downloaded the dvd, and now I've installed through the graphical mode. But I'm missing the new startup (without grub), can't recall what it's called. 

And where did vpnc go???

---

