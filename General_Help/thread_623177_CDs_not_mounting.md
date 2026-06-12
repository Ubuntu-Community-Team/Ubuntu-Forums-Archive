---
title: "CDs not mounting"
date: 2007-11-25
forum: General Help
---

### Post by petersjm on 2007-11-25
Hi guys. Firstly, I've gone through previous threads but can't find anything similar to this:

I was going through my old CD collection and decided to add a few of the CDs to my HDD to play in Amorak. All were mounting and copying fine, except for two CDs from the same artist: Nelly Furtado. Both her first (?) album "Whoa, Nelly" and the next one, "Folklore", when I put them into my CD drive, nothing happens. The drive doesn't mount and the CDs aren't shown. It's like there's nothing in the drive.

All other CDs (so far) are working as they should. I'm sure I was able to copy these Furtado CDs on Windows, but I haven't been on Windows in so long that I could be mistaken... I figured maybe it was a DRM thing? I'm not sure. Any ideas how I can get these CDs to show up so I can copy them? Anyone ever come across this before?

Mounting /media/cdrom0 doesn't work in these cases. Any other ideas? Thanks :D

(Oh, PS, it's not just an Ubuntu thing; I tried it in OpenSUSE too and the same thing happens - or, rather, *doesn't* happen...)

---

### Post by bettlebrox on 2007-11-25
Maybe the CD's are copy protected?

Do you see anything in the logs when you put the CD's in the drive?

---

### Post by petersjm on 2007-11-26
> **bettlebrox said:**
> Maybe the CD's are copy protected?

Do you see anything in the logs when you put the CD's in the drive?

Thanks, Bettlebrox. I thought it might have been a copy-protection issue (which brings up the *other* question about allowing a backup copy etc!). Which logs are you referring to and I'll check when I'm home tonight?

---

### Post by bettlebrox on 2007-11-26
You can look at the output of the command dmesg . Or look at these log files:
/var/log/messages
/var/log/kern.log

---

