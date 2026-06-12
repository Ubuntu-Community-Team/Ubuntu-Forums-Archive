---
title: "Jigdo downloads how to resume?"
date: 2008-06-19
forum: General Help
---

### Post by skralljt on 2008-06-19
I've been messing around with jigdo the last few days (Comcast must have their eye on me by now) downloading the hardy heron dvd iso.  I have become tired of ubuntu not playing dvd's, but not enough to abandon ubuntu.  Well, I run jigdo-lite, download the whole thing, and it filled up the drive I opened jigdo-lite on.  So I move the downloaded files which now total 4.5 GB and try to resume by:
> Under Linux, you can loop-mount the .tmp file to access the packages that were already downloaded, and reuse them for generating an image from a newer .jigdo file. To do this, first issue the following commands as root in the directory with the broken download: mkdir mnt; mount -t iso9660 -o loop *.tmp mnt. Next, start a new download in a different directory, and enter the path of the mnt directory at the "Files to scan" prompt.
(from [http://atterer.net/jigdo/debian-jigdo-mini-howto/x347.html#AEN384](http://atterer.net/jigdo/debian-jigdo-mini-howto/x347.html#AEN384))

I have successfully mounted the temp file and have told jigdo-lite the location of the mounted temp file when it asks, as well as the location of the original temp file.  Neither works, downloads always resume at 0.  Torrents are way easier to use than this crazy program, I wish that there was a torrent for daily builds of the hardy dvd.  The funny thing is I am trying to save canonical bandwidth by repeatedly downloading a dvd, all because jigdo is so hard to use.  Must have cleared ten gigabytes in a few days by now!  Does anybody know exactly what directory to point jigdo to for resuming?  The old download directory, the loop mount, etc?  




Problems I hope to fix with a new install:  
After login, blank screen with mouse (gdm freezes?)  
Cannot play encrypted dvds, even after walkthroughs and esoteric scripts
Putting mysql on a faster drive, so that it takes up less than 50% cpu when running amarok without scripts.

---

### Post by vigyani on 2008-06-22
Hi

I use Jigdo-lite to download. I have downloaded Hardy and using it updated to the daily DVD 8.04.01 or Edubuntu etc. without any problems.

I am not able to understand what problem exactly you faced. If you give more information may be I can help.

regards
vig

---

