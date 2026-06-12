---
title: "rsync - safe to run multiple rsyncs at once?"
date: 2020-08-29
forum: General Help
---

### Post by fluffy20470-50233 on 2020-08-29
I want to backup many hard drives on my desktop pc (locally). Can I for example run the following at the same time?:

```
rsync -r --info=progress2 /media/username/hdd1a /media/username/hdd1b
rsync -r --info=progress2 /media/username/hdd2a /media/username/hdd2b
rsync -r --info=progress2 /media/username/hdd3a /media/username/hdd3b
```

Or can running multiple rsync tasks at the same time mess something up?

---

### Post by TheFu on 2020-08-29
Perfectly fine, if the system can take the I/O. 
I tend to do them in sequence using -avz options.  The flaw is that deleted files in the source don't get deleted in the target areas without more options.

Hopefully, this is only for huge media files.  rsync really isn't sufficient for a backp solution for the OS or normal end-user files that change over time. There are better tools.

---

### Post by fluffy20470-50233 on 2020-08-29
> **TheFu said:**
> Perfectly fine, if the system can take the I/O. 
I tend to do them in sequence using -avz options.  The flaw is that deleted files in the source don't get deleted in the target areas without more options.

Hopefully, this is only for huge media files.  rsync really isn't sufficient for a backp solution for the OS or normal end-user files that change over time. There are better tools.

Thanks! It's just a 1 time copy from my old HDDs (which I will no longer use) to my new HDDs. I'm just using rsync because I figured it'd be safer than using a GUI file manager. 

If you have a better command then I'm open to suggestions!

---

### Post by TheFu on 2020-08-29
> **fluffy20470-50233 said:**
> Thanks! It's just a 1 time copy from my old HDDs (which I will no longer use) to my new HDDs. I'm just using rsync because I figured it'd be safer than using a GUI file manager. 

If you have a better command then I'm open to suggestions!

Yep, rsync is the correct tool.  Just run it with sudo to keep owner, group, permissions. et al.  One of my actual media mirroring commands:
```
sudo ionice rsync -av --stats --progress $EXCLUDES --delete /d/D1/ /d/b-D3/
```

This is specific for media files (plex server) that gets mirrored a few times a week between disks directly connected to the same computer.  If it was over a network, the command would be slightly different to use rsync in a smarter way.  Speed isn't as important as not completely taking over the CPU and I/O of the system, which is doing many other things too.  It is the LAN nextcloud, calibre, nfs, znc, wallabag server too. Plex Server is just 1 of the tasks it does.

Best to learn and understand the use of the trailing '/' on the source argument too. In rsync, that character matters.

---

