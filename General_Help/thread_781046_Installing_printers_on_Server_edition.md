---
title: "Installing printers on Server edition"
date: 2008-05-03
forum: General Help
---

### Post by sluthy on 2008-05-03
Once I get my new Hardy Server install up and running (see other thread in Install forum), I want to install two printers for network sharing. I see a lot of How To's that use wizards and stuff, but it's all GUI, and AFAIK Server edition only includes CLI.

How do I go about doing this?
HP LaserJet 1200 (should be easy)
Canon PiXMA iP5000 (could be trouble)
Both USB

---

### Post by jimv on 2008-05-03
Does this help?

[http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

---

### Post by sluthy on 2008-05-04
That does help a lot, thanks. I was reading a few days ago about Hardy having CIFS as well now, which makes Windows sharing easier, where CUPS with Windows "will still need some work." Does this affect me at all, can CIFS help me out here?

---

### Post by sluthy on 2008-05-04
I have the LaserJet working! Hooray!

1. How can I print a file from a prompt? Say, if I wanted to run off cupsd.conf, how would I do that?

2. When I add the printer to a Windows PC, it comes up "Access denied, unable to connect", but it can still print fine. They are in different workgroups, does that matter?

3. Is there any problem with having different drivers? Because adding it to a Windows PC comes up with "this print server does not have the correct driver", and I have to select the "right" one from the list (I just choose HP LaserJet 1200 PCL). Is that fine, because I noticed the print quality is less than stellar (passable, but it's a bit faint and pictures are a bit muddled) and I'm not sure if it's the printer/toner or the drivers.


4,5,6... How about the Canon? I've read heaps of stuff about the love/hate relationship between Canon and Linux, particularly the PiXMA line. The HP was easy because the PPD was pre-installed. What now?

---

