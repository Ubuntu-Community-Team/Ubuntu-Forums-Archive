---
title: "Tracker doesn't search anything"
date: 2008-07-06
forum: General Help
---

### Post by iampriteshdesai on 2008-07-06
Tracker doesn't show any thing. I tried to reset it with some command but still doesn't help

---

### Post by ryanhaigh on 2008-07-06
How are you trying to search?
What version of Ubuntu are you using?

---

### Post by iampriteshdesai on 2008-07-07
I am using hardy. I am using the usual application>Tracker

---

### Post by harshpshah on 2008-07-10
> **iampriteshdesai said:**
> I am using hardy. I am using the usual application>Tracker

Same here.  Index statistics shows 13502 files, 883 text, 6 videos, 1 music file etc. When I search for anything, nothing comes up. I have tried really simple words like a, an, the etc. as well as words and phrases I definitely know are in the indexed files. The search window just stays empty. I'm using hardy by the way. I was using beagle on gutsy very happily, except I read that tracker lets you tag your searched files, and was eager to try out that functionality.

---

### Post by Gatemaze on 2008-07-16
Yes I am also on the same boat with tracker.... it is supposed to be looking the filenames too which apparently it does not... It does display though metadata... Btw, have you run tracker-preferences to setup which directories should be indexed? Home dir is indexed by default.... also try catfish for simple file search... and if install tracker-utils you can use catfish with tracker as the backend...

---

### Post by redrocketb on 2008-07-28
Aw, man, I thought for sure this was just an issue for me on my new install on a Toshiba (U205). Tracker has had the same issue since I installed. I tried uninstalling and reinstalling, and after doing so I had a few results (tried searching for files on the desktop and *.mp3 with some results). Closed client, opened again, no results.

Details: Hardy, Tracker 0.6.6. Have explicitly set it to search desktop and my document folders on my NTFS partition (want to keep them there so Windows can see them too). At first I thought it was an NTFS issue, but didn't find anything like that from Googling, and more important the initial search after reinstall (for mp3s) found results on the NTFS partition. 

Really a pain--I recently converted from Windows and wanted a free Google desktop replacement. But now I see that others are having the same problems. Any suggestions on another app?

---

### Post by ryanhaigh on 2008-07-28
I'm personally not a fan of indexed search but if you are looking for a google desktop replacement well look no further than....[google desktop]("http://desktop.google.com/linux/index.html").

---

### Post by redrocketb on 2008-07-29
Oh, believe me, I've installed it. Just looking for free software alternatives (and lamenting the fact that the search tool that comes with Hardy doesn't appear to work).

After resetting, had same thing happen again: first time I ran tracker search, could see results for desktop and same 30 mp3s. Ran a few more searches, no more results at all. Frustrating.

---

### Post by halucard22 on 2008-07-29
Same here. For me, Tracker is a big joke. It runs but it's unusable. I prefer Beagle, and the hardy version is much better than the previous versions. So, i recommend "Beagle" for the files indexer, at least on Ubuntu Hardy.

---

### Post by chris4585 on 2008-07-29
use beagle it actually finds things unlike tracker does

```
sudo apt-get install beagle
```

then look in applications > accessories > search

---

