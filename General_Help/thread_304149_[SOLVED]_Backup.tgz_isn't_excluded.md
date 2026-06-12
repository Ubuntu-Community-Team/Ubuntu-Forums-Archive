---
title: "[SOLVED] Backup.tgz isn't excluded"
date: 2006-11-21
forum: General Help
---

### Post by Interestedinthepenguin on 2006-11-21
Hello everyone.  

I've been trying to backup my Ubuntu installation.  

I've followed the instructions in the 'Backup and restore your system!' tutorial, but backup.tgz won't exclude. :-?  

Can someone help me out, please?


--Nevermind, problem solved.  

I was adding ```
--exclude=/media
``` even after unmounting the drives in /media.  

My backup.tgz was excluded after I took that out.

---

