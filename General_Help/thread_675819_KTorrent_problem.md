---
title: "KTorrent problem"
date: 2008-01-23
forum: General Help
---

### Post by dynamethod on 2008-01-23
Hi there ive been using Ktorrent, yesterday it worked fine, today it wont connect to any trackers

the trackers are not down, i have the IP blocker plug in installed and using a blocklist from peergaurdian sources,

the status of the torrent says "stalled"

and heres what the log viewer says:

Loading Anti-P2P filter...
AntiP2P header loaded.
IP 0.0.0.0 banned.
Multi file torrent
OutputPath = /home/user/Bass - Dark Trance -- Jamendo - OGG Vorbis q7 - 2006.06.10 [[www.jamendo.com]/](www.jamendo.com]/)
MultiFileCache::preallocateDiskSpace

im downloading a legal torrent by the way,

im using Kubuntu 7.10

is there something i should be changing in the settings?

help much appreciated

---

### Post by bluesrocker on 2008-01-23
I'm new to Linux, but there is one thing that I am positive of, this information (IP 0.0.0.0 banned.), you don't have an IP on you computer. The 0.0.0.0 is usually a NIC card problem, make sure you can check the card. Can you surf?

---

### Post by wolfen69 on 2008-01-23
can you surf the net?

---

### Post by wolfen69 on 2008-01-23
maybe the peerguardian file is screwing things up. try this:

here is the link to level1 (p2p) zip file. [http://www.bluetack.co.uk/forums/ind...ewcat&cat_id=4](http://www.bluetack.co.uk/forums/ind...ewcat&cat_id=4) to use in ktorrent, it must be unzipped first, leaving you with a level1.txt file. then just point ktorrent to where the txt file is. then convert file. hit apply.

---

### Post by dynamethod on 2008-01-23
Yeah its definatly Ktorrent not my connection/NIC, because i tried Azureus, and that works fine, but Ktorrent refuses to budge anymore, no worrys though just using Azureus now

---

### Post by XopherH on 2008-04-25
> **wolfen69 said:**
> maybe the peerguardian file is screwing things up. try this:

here is the link to level1 (p2p) zip file. [http://www.bluetack.co.uk/forums/ind...ewcat&cat_id=4](http://www.bluetack.co.uk/forums/ind...ewcat&cat_id=4) to use in ktorrent, it must be unzipped first, leaving you with a level1.txt file. then just point ktorrent to where the txt file is. then convert file. hit apply.


here is an updated link to the Level1.txt.zip that worked for me just now.  Happened upon all this after the upgrade to 8.04.

[http://www.bluetack.co.uk/forums/index.php?act=dscriptdl&CODE=dodownload&f_id=178b88ce4c4733331d632d9fd638c01661](http://www.bluetack.co.uk/forums/index.php?act=dscriptdl&CODE=dodownload&f_id=178b88ce4c4733331d632d9fd638c01661)

---

