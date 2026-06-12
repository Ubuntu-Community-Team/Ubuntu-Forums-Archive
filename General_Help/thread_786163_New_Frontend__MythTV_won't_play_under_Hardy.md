---
title: "New Frontend:  MythTV won't play under Hardy"
date: 2008-05-07
forum: General Help
---

### Post by Weidbrewer on 2008-05-07
I put together a frontend out of some spare parts and - after issues with 7.10 and Mythbuntu 7.10 - I ended up installing 8.04, and downloaded mythtv's frontend + plugins.

Everything fires up properly, and I am able to see recordings and videos on my backend (another machine) but when I hit play, the screen goes black,nothing ever plays, and then the machine locks up.  Any ideas?


System specs:

766Mhz Intel
524MB RAM
ATI Radeon 9200 (with restricted driver.)
40GB HDD
Standard 3COM ethernet card

Also of note, I have another frontend on the network, and everything works fine with that one - so what ever the problem is, it's local to this machine.

---

### Post by Weidbrewer on 2008-05-10
Turns out that it was the restricted ATI driver...if I disabled it, everything worked fine.

---

