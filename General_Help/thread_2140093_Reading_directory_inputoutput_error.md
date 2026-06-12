---
title: "Reading directory input/output error"
date: 2013-04-28
forum: General Help
---

### Post by ravaned on 2013-04-28
So, for the past few months I've been using 12.10 and was happy to move on to 13.04 after all the trouble 12.10 has proven to be on many occasions, this also being the reason why I decided to do a clean install.
I moved all the movies and documents that I wanted to save to an external drive (NTFS) but on several occasions the copy process just froze and I had to unplug the drive and plug it back in. Eventually I did manage to copy all the stuff and it was visible in nautilus.

I then did the clean install of 13.04 and when I tried to access on the external drive, there was nothing, nautilus shows it empty and from the terminal I get "ls: reading directory .: Input/output error". I tried from Windows7 but all I got was "cyclic redundancy error" or something like that.

I've looked the terminal error on google, but most of what I found suggested using smartools (which I did and the external drive is healthy) or formatting the drive (which is not the case since the rest of the data on it is intact).
Is there any way to recover the lost data or should I just give up?

Edit: solved it. after going through all sorts of recovery programs like testdisk and gddrescue, I got every single file that was ever deleted on the external drive except the files that were in that folder. Out of despair I switched back to windows and ran chkdsk which solved the problem.

---

