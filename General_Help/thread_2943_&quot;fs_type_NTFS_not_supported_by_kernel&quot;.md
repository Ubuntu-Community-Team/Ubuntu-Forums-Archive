---
title: "&quot;fs type NTFS not supported by kernel&quot;?"
date: 2004-11-02
forum: General Help
---

### Post by Caudata on 2004-11-02
I just edited my fstab in order to mount my NTFS partition. I used the following statement in fstab:
/dev/hdb1     /media/windows   NTFS   ro,dmask=0222,fmask=0333   0 0

Also, I created a /media/windows directory, and I did mean hdb1. After restarting upon booting I saw the statement in the subject line "fs type NTFS not supported by kernel". What is going on any suggestions? I've been reading of people being able to read their NTFS partition, and as far as I know the statement should have worked. I'm using Ubuntu 4.10. Any suggestions on how to fix this would be appreciated, thanks in advance!

                                                                                                       -Caudata

---

### Post by diebels on 2004-11-02
try lowercase ntfs

---

### Post by userX on 2004-11-02
yup, lowercase ntfs will do it

---

### Post by Caudata on 2004-11-02
I reread what I wrote I looked at that and said DOH! The problem was the caps in NTFS. I can see my windows partition now thanks for bearing with the Linux noob!


                                                                                                    -Caudata

---

### Post by diebels on 2004-11-02
Typos are very "Human"  ;)

---

