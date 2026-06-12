---
title: "ATI fglrx problems"
date: 2004-12-17
forum: General Help
---

### Post by flibblesan on 2004-12-17
I've been posting about this in the HOWTO ATI thread but I guess nobody reads that :D

I've tried for a long time to get the recent ATI drivers working, both flavio and Daniels files. But each time I can't get direct rendering and only Mesa. But if I use the 3.12 drivers from Warty they work fine.

I've followed all the howtos to the letter and done everything the same with each set of drivers I've tried and I've fully removed each one to try the next etc.

So why dont they work? Is there something different in the Warty ones that the others are lacking?

---

### Post by daniels on 2004-12-18
I don't know -- the last time I was at home, where I have a Radeon, was a good seven weeks ago, so I haven't been able to test them myself, but others report that they're working.  If you file a full bug report with the output of /var/log/XFree86.0.log and /etc/X11/xorg.conf at [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com), I'll take a look at it in a bit.

I'm on holidays from yesterday until the 2nd or 3rd, so I'm taking the opportunity to catch up on sleep (fd.o and Ubuntu have both kept me very, very busy lately), get myself back home and then recover from the jetlag, see family + girlfriend + friends again, so I doubt I'll get to look at it until the new year or such.  So hopefully it gets solved before then; if not, I'll check it out.

---

