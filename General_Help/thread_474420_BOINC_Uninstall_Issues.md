---
title: "BOINC Uninstall Issues"
date: 2007-06-15
forum: General Help
---

### Post by foxmulder881 on 2007-06-15
I installed BOINC on my system to find that it's just not as stable as the Windows version. Now I have the problem of trying to uninstall it. Every time I try to uninstall it, I get the error message...

> E: boinc-manager: subprocess post-removal script returned error exit status 139

What is this error and how do I completely remove it from my system?

---

### Post by lonoy on 2007-06-15
Sorry but I have never tried to uninstall the Boinc Manager. I have upgraded it with success though this week, maybe you could give that a go to see if it improves the situation.

[http://ubuntuforums.org/showthread.php?t=470458&highlight=boinc](http://ubuntuforums.org/showthread.php?t=470458&highlight=boinc)

Cheers
Lonoy

---

### Post by foxmulder881 on 2007-06-15
I tried that lonoy and it doesn't work or help in any way.

I think it's broken my whole Synaptic Package Manager somehow. Because now I can't even do a system update via Update Manager.

UPDATE: I managed tp update to the latest BOINC client and manager using the deb packages d/loaded from [www.getdeb.net](www.getdeb.net). Attempting to uninstall with the new version, I am presented with the same error message.

This is really starting to piss me off...

ANOTHER UPDATE: It seems that I'm talking to myself here but I'll update anyway for archival purposes.
I finally fixed the problem after over approx. 8 hours of trying different things. I found another (old) thread here...
[http://ubuntuforums.org/showthread.php?t=81598&highlight=boinc+uninstall](http://ubuntuforums.org/showthread.php?t=81598&highlight=boinc+uninstall)

So I thought it would be worth a shot to remove ALL files related to BOINC. So I logged in as root, searched for anything related to BOINC, deleted all related files. And blow and behold, it worked. BOINC is now completely removed from my system.

Seriously, if your ever thinking about installing this buggy piece of software that is suppose to do good for all mankind, PLEASE DON'T! It'll give you the biggest Ubuntu headache you'll ever experience.

End of discussion!

---

