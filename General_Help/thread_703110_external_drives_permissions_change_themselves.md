---
title: "external drives permissions change themselves"
date: 2008-02-21
forum: General Help
---

### Post by matthekc on 2008-02-21
I have an external drive that i chmod -r 777 quite regularly because permissions keep changing to owner read write.  I saw a post on the suse forums that a guy had a similar problem with a local file and changing his /etc/permissions was the fix.  I'm not going to try right now but I'm curious if that would fix my problem.

---

### Post by SpaceTeddy on 2008-02-21
what filesystem does your external harddrive use ? 

and i cannot find any /etc/permissions on my computer, so i fear that was a suse fix...

---

### Post by matthekc on 2008-02-21
its vfat 
rw nosuid nodev uid=1000 fmask=0077 dmask=0077  the rw in there does that mean read write perhaps thats the problem

---

### Post by SpaceTeddy on 2008-02-21
vfat cannot save ANY file permissions (the file system does not support it). so no matter what you set, it will always go back to the default you defined.
The default ist set by the fmask and dmask... i am not mistaken, change them fmask=0111 and and dmask=0000 and your permissions should be what you want them to be.

---

### Post by matthekc on 2008-02-22
I'll try that later thanks

---

