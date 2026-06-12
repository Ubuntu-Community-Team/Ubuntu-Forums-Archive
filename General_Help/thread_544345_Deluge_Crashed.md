---
title: "Deluge Crashed"
date: 2007-09-06
forum: General Help
---

### Post by RhubarbnCustard on 2007-09-06
Just installed Deluge and it was happily purring away d/ling 3 torrents I'd started before with Freeloader (which I uninstalled because it wouldn't continue any files after a restart). Now, after a restart, when I run Deluge I get the following errors:

steve@scragglemuffin:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
No DHT file to resume
Torrent Size 314031719.0
Available Space 11031023616
Torrent Size 367014846.0
Available Space 11031023616
Torrent Size 730468098.0
Available Space 11031023616
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)
steve@scragglemuffin:~$ 

I thought the problem might be that /tmp was too small but I don't think that's the issue as the problem resembles crashes I've had with Ktorrent and Azureus on 2 different machines. /tmp is 1gig on it's own partition btw.

Oh, just before I shutdown I moved a torrent down to the bottom of the queue and it disappeared (still physically on the drive though). Looking at my d/l rate I noticed that it was a lot higher than for the 2 remaining d/ls so I think the 3rd was still d/ling somewhere in the background.

Any ideas would be appreciated.

Thanks

---

### Post by RhubarbnCustard on 2007-09-06
Okay found a fix:
[http://ubuntuforums.org/archive/index.php/t-387541.html](http://ubuntuforums.org/archive/index.php/t-387541.html)

Still lost my d/ling torrents though

---

### Post by RhubarbnCustard on 2007-09-06
No I didn't - they still work :))

Think I'd better shutup now!!!!

---

