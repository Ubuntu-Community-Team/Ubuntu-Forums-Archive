---
title: "Ubuntu freed up some space in &quot;/&quot; by itself somehow?"
date: 2008-03-17
forum: General Help
---

### Post by HunterK on 2008-03-17
Hey all.  I have proof via screenshot that my "/" partition had 4.38 GB used yesterday.  Now, today, after moving a bunch of files around from an old ntfs partition to /home/userid, it is down to 3.34 GB used??? 

What happened where it freed up over 1GB of space?  Was there some sort of cache being cleared? Maybe I took the screenshot when there was a ton of temp / cache stuff built up and now that I rebooted its cleared? :confused:

---

### Post by DoctorMO on 2008-03-17
the only thing that gets cleared when you reboot is /tmp although I'm hopeful that ubuntu has a way of reclaiming the space used by cached packages. so far I've not see it though.

---

### Post by Pijits_1 on 2008-03-17
Ya could be that the /tmp was cleared after reboot, or the system has evolved past just a normal operating system :O

Another possibility is that trackerd was running and discovered that you didn't use up that much space, trackerd is an indexing tool.

---

