---
title: "Error 15 after power outage - have I hosed my system?"
date: 2008-06-27
forum: General Help
---

### Post by dash2 on 2008-06-27
Hi

I ran out of battery power while using a wubi-based installation of Hardy. When I tried to reboot I got "Error 15, file not found" from Grub. I booted into Windows and ran "chkdsk /r" but I still don't have anything in my C:/ubuntu/disks folder... in fact I don't even have a disks folder any more! And I can't find any folders called "found000" where my disks might have been moved to.... is there any way I can get back my Ubuntu data?

Cheers
David

---

### Post by dash2 on 2008-07-03
Replying to myself here.

If this happens to you and you run 'chkdsk /r' and still can't find your wubi files, check very hard. Even if I turn on "view hidden and system files" in Windows Explorer, I **still **don't see the folder "found.000". However, the folder is visible (and taking up 8 gigs!) in [windirstat]("http://windirstat.info/") and if I navigate in Windows Explorer to c:\\found.000 then I find my stuff is still there... so I'm going to try and reinstall it :guitar:

---

