---
title: "Ubunt 6.06 vs. Ubuntu 6.10 Minimal vs. Ubuntu 6.10 Standard"
date: 2007-02-07
forum: General Help
---

### Post by Trickyphillips on 2007-02-07
I'm moving away from shared hosting to a VPS, on which I plan to host my own website, forums, Shoutcast server and maybe a light game server. I've used Debian on a dedicated server in the past, but I'm interested in giving Ubuntu a try this time.


In the VPS control panel, I have the choice of installing the following:

Ubuntu 6.06
Ubuntu 6.10 Minimal
Ubuntu 6.10 Standard


I want to be sure I'm making the right choice, so I'd like to know a few things...

From what I understand, 6.06 would be a good choice if I'm looking purely for stability, but 6.10 will be more current, right? What is the difference between 6.10 Minimal and 6.10 Standard? Does the standard edition of the server ISO include Xorg, Gnome, etc.? A GUI would be a waste of RAM for me, obviously. I don't plan on tunneling X over SSH.

Which installation would you guys suggest? 

Thanks.

---

### Post by dexter on 2007-02-07
6.06 is considered more stable than 6.10 (*Edgy* Eft), for a server i would recommend Ubuntu 6.06 server, which doesn't come with a graphic environment (but you can install it afterwards, if wanted), so no waste of ram on that.

---

### Post by fragos on 2007-02-07
It would seem logical that something that's been out there longer would be more "debugged" and stable.  There is however a trade off.  Some difficult to fix and less critical problems may not have been fixed in the older release.  6.10 has been out for a while so IMHO I'd use it unless I planned to not upgrade in the future and wanted to insure long term security fixes.  In that case 6.06 is better.  As to which is better, 6.10 minimal or standard, minimal is a subset of standard and become "standard" if you add what you need.  IMHO, unless I was hardawre limited I'd choose "standard".

---

