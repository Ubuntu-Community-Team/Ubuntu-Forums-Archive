---
title: "Ubuntu 14.04 LTS: Firefox can't open profiles on server"
date: 2014-06-28
forum: General Help
---

### Post by ExNASATerry on 2014-06-28
I've always kept my Firefox profiles on my Network Attached Storage devices (currently a Netgear Ultra 4). I just got a new computer with Ubuntu 14.04 LTS pre-installed. Firefox opens the "default" (local) profile fine, but any time I try to open any of my profiles on my server, it fails, telling me the profile is in use. It seems to create the .parentlock file _before_ checking to see if it's already there! (I'm not sure that's what is, in fact, happening, but that would fit the symptoms.) I check the server and the .parentlock file is there. I delete it, try opening the profile again, get the same message, and yep, the .parentlock is back.

This happens for all three of my remote profiles, but as I said, not the locally stored one. It does not happen with my other boxes (Ubuntu 12.04, Windows XP, Windows 7), only the new Ubuntu 14.04 LTS box. I'm running Firefox 30.0.

Help???

---

### Post by TheFu on 2014-06-28
Are you trying to run Firefox from different machines concurrently?

I don't know the answer, what changes there are in Firefox file locking requirements and how that interacts with the NAS capabilities.

So ... 30 seconds of google have me believing that if it worked previously, it was a bug. The intent is for only 1 active firefox to have a profile open at any time. This is to prevent profile corruption. When firefox is closed, the lock file is removed.  That's the theory.

Might be helpful to know how each remote system is connecting to the NAS - NFS (v3, v4?), CIFS?  Though I don't think it will help.

---

### Post by ExNASATerry on 2014-06-29
Yes, I'm running only one instance of FF at a time. Firefox v. 30.0 works fine under Windows, even the Windows VM I'm running under Ubuntu 14.04, but not under Ubuntu itself. Clearly a problem with either FF or Ubuntu 14.04 LTS. Maybe I could try installing an older version of FF on my Ubuntu box, see if that works....

---

### Post by TheFu on 2014-06-30
I tested this on my netbook - it worked here too with the local storage.  I moved the lockfile, started a new firefox instance - expected to see the lock file replaced, but it wasn't.  Hummmm.

I do have some NFS storage (12.04 NFS v4 server), that I'll try to test with, if I can figure out how to force a different profile directory.

BTW - the man page for firefox has some options that might be helpful, though it is fairly lite on content for the program (it isn't ssh). **man firefox** to see them.

---

### Post by ExNASATerry on 2014-07-06
So once again, the Ubuntu forums come to the rescue. I'm trying to recall in the ~5 years I've been coming here (under a couple of different names), if I've ever gotten useful help. None comes to mind.

---

