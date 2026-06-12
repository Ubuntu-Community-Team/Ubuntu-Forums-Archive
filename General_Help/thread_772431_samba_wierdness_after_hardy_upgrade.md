---
title: "samba wierdness after hardy upgrade"
date: 2008-04-28
forum: General Help
---

### Post by trmentry on 2008-04-28
I'm having an odd Samba thing on my upgraded laptop after going to Hardy.

On Gutsy, I had gone to Places -> Connect To Server

And mapped 3 Samba shares on a fileserver.   This placed the mapped shares as an icon on my desktop.  

After the upgrade the icons were gone.  I expected this.  (Note: In Gutsy when I booted the laptop it would automagicly put the icons back.)

Anyway.. I went to map them again.  I enter in the server, share, username, and domain.  It then comes up with smb error but still puts the icon on the desktop.  I double click on it and it creates another icon on the desktop.  Both seem to work.  

I messed around and unmounted them all.  I then remounted only giving the server and share this time.  And it makes the icons single now.  My username on laptop is the same as the samba shares so figure that would work.

But I'm curious as to why when I enter my username in the field it makes 2 icons.

Any ideas?   (is there some file that needs to be cleaned up or config'ed after the upgrade)


Thanks

---

### Post by rturner on 2008-04-28
I did a clean install and noticed the same behavior, but for only one of my shares;  the rest mount normally.  There were some bug reports relating to nautilus/network weirdness, and I'm assuming it's something that will get fixed and be updated.

---

### Post by trmentry on 2008-04-28
Thanks for the reply.  I'll keep my eyes open on update mngr.  :)  

This issues isn't overly worrisome as I can get to the files I need...just was annoying getting duplicate icons.

---

### Post by Thorun on 2008-04-28
Hi. 

I have the same issue. But i'm not used to fix problems myself... I can't get around this problem. 

I noticed, that in the live session user - the network-drives works wery well. But when i install the 8.04, it doesn't work anymore. 

Is there someway, i can copy the settings in the live user session to a fresh 8.04 install - and that way make it work?

---

### Post by vishnu on 2008-04-28
My issue is that everythiong appears to be fine when I create a share but I can't see it from another box or even my own in network browser.

I can see my PC on network, usershares folder has share info, smbclient, smbfs, samba all installed.  didn't get this problem in beta.  only since i've installed from cd and network share options is different.
if anyone has ANY ideas please let me know as I'm considering re-install or going back to gutsy at this point.

---

