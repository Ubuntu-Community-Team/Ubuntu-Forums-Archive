---
title: "A few questions regarding a &quot;server&quot; per se."
date: 2007-04-22
forum: General Help
---

### Post by Roasted on 2007-04-22
I've got a linksys router, 4 ports, and 4 computers here. So the router is full. I was just given an old compaq presario. I have a 200 gig spare hard drive sittin on the shelf behind me.

I was thinkin... is there anyway to hook up this compaq to the network and have it just sit and run 247 and be some kind of a backup server? I want it to run linux, and to allow windows machines to write to it.

And as far as getting around the 4 port problem, I just need to get a switch and plug into the router, then plug in the compaq to the switch. Right?

---

### Post by DoktorSeven on 2007-04-22
Yep, no problem.  Install Linux on it, install Samba to allow Windows machines to access it as a network share (or use FTP, or any other means of file sharing with it). 

As for the network, exactly.  Grab a switch, plug it into the router, and it will act as more ports for the router.

---

### Post by Roasted on 2007-04-22
Will having a computer plugged into the switch yield in less of a reliable connection as opposed to being plugged straight into the router?

Also, I'll give samba a shot... I tried getting samba set up on this computer a few weeks back and I wasn't able to get it to work, and nobody on these boards knew what was happening, so it was never fixed. *shrug* I'll give it a shot.

But I don't need a linux server OS or anything, just straight up Ubuntu?

---

### Post by dcstar on 2007-04-22
> **Roasted said:**
> Will having a computer plugged into the switch yield in less of a reliable connection as opposed to being plugged straight into the router?

Also, I'll give samba a shot... I tried getting samba set up on this computer a few weeks back and I wasn't able to get it to work, and nobody on these boards knew what was happening, so it was never fixed. *shrug* I'll give it a shot.

But I don't need a linux server OS or anything, just straight up Ubuntu?

Don't be concerned about where you plug things into, unless you are saturating the network links this sort of thing won't be an issue.

There are specialist Ubuntu server CD images you can download that make a server install easy.

---

