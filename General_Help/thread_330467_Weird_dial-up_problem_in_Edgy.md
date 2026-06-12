---
title: "Weird dial-up problem in Edgy"
date: 2007-01-03
forum: General Help
---

### Post by Bartender on 2007-01-03
I did a search on this and see that several people are reporting problems after going to Edgy, but didn't see anything that matched what I'm experiencing.
Using an external USR Sportster in Dapper, I went into Networking, plugged in the settings, added Modem Monitor to the upper panel, and was connected.  Haven't used and am not familiar with wvdial, gnomeppp, or whatever other options exist.

In Dapper, under the Modem settings, it's set to 'Tones', not 'Pulse'.  

In Edgy (the exact same thing happened with Ubuntu and Mint Bea) I click 'Tones', finish the settings, close out, go back, and it's set to Pulse instead.  WTH??!

So, first off, has anyone else experienced this, and what did they do?  

Second, I cannot figure out how to wipe the settings and start over.  No matter what I try Networking holds onto the original settings like a drowning man clutching a life raft.  Any ideas?

Third, Modem Monitor never gives me "Activate".  It's always grayed out.

If other people have experienced the same problem with Tones changing to Pulse on its own, I'll report as a bug.

For the rest of it, any help much appreciated.

---

### Post by _duncan_ on 2007-01-03
I don't dial-up using System > Administration > Networking (I prefer gnome-ppp or kppp), but after reading your post I decided to try it out.

I can confirm that the same thing happens to me using Edgy, so it's probably a bug.

---

### Post by Bartender on 2007-01-03
Thanks, duncan -
The original post flew off the front page in minutes, so didn't know if anyone would even bother to respond, much less take the time to check it out.

Is gnome-ppp built into Edgy, and if so, how do you bring it up?  Hope there's no downloading involved, for obvious reasons...

---

### Post by _duncan_ on 2007-01-03
gnome-ppp is available from the ubuntu repos only. For fresh installs without net connection, it's better to use pppconfig or wvdial first, then install gnome-ppp once an initial connection is made.

click on the 2nd link on my signature (Dial-Up Modem Wiki) to learn more about those 2 commands. I personally prefer pppconfig (with pon and poff) coz it always sets the /etc/resolv.conf file correctly unlike wvdial.

---

