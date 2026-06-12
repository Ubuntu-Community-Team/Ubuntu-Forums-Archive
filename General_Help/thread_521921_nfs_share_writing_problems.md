---
title: "nfs share writing problems"
date: 2007-08-09
forum: General Help
---

### Post by notatoad on 2007-08-09
i have an nfs share on my fileserver mounted on a folder in my home folder (/home/kyle/movies) and i can read from it fine, the folder has 777 access and is owned by root.  when i try to copy files to the folder, i get a message saying "operation not permitted", and i click retry.  i then get a message saying "the file already exists" and i click overwrite and it copies fine.  

how can i get it to copy without the stupid error messages?

here is the fstab line to mount the share:
```
192.168.1.147:/mnt/320/movies 	/home/kyle/movies 	nfs rsize=8192,wsize=8192,timeo=14,intr,user 0 0
```

oh, and chown is not permitted when i have it mounted, and owner reverts back to root when i mount the share

---

### Post by jpeddicord on 2007-08-12
That sounds like a bug. Could you please search for it at [http://bugs.launchpad.net](http://bugs.launchpad.net), and if you cannot find it, report a new one?

Jacob

---

