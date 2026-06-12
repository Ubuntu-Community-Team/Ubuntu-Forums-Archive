---
title: "Netatalk pkg won't install or be removed"
date: 2007-06-09
forum: General Help
---

### Post by jrcal on 2007-06-09
I'm rather new to linux.......have the netatalk package, which was working, stopped working, I tried reinstalling and screwed it up.   Now I get errors trying to reinstall or remove.   I have found many threads with people having similar problems with various packages, many of which were not resolved.  Using apt-get, aptitude, and dpkg with various options like install, remove, purge, force, autoremove, --configure, etc, the errors are always similar:

invoke-rc.d: initscript netatalk, action "start" failed.

subprocess post-installation script returned error exit status 1

I deleted all the K50netatalk and S50netatalk files from the /etc/rc*.d folders and tried re-installing, but the same thing happens.   

I'd love to have my AFP server, but I'm absolutely stumped.  Would love any help anyone might have, thanks!

Justin

---

### Post by pinkpanther_bc on 2007-09-23
I have the same problem and have had it since upgrade to *Feisty, upgrading to Gutsy now and it still gives me the same issue.
E: /var/cache/apt/archives/netatalk_2.0.3-6ubuntu1_i386.deb: subprocess new pre-removal script returned error exit status 1 this is the message, I would apreciate any help to solve this problem

---

