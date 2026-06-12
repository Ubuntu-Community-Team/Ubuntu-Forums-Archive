---
title: "fsck information please"
date: 2006-11-10
forum: General Help
---

### Post by btboudreaux on 2006-11-10
Does anyone know where to find any guides and information for fsck?

I tried the wiki and google but didn't find much. I also read the MAN pages, but would like something not as cryptic.

The reason I ask is, I'm considering turning my XP "server" at home to Ubuntu. The only reason I haven't done so yet is because I have lots of important data (by important I mean pictures/mp3s/comics) on it and I want to be able to check the disk to make sure everything is healthy and bad sectors are caught and possibly recovered. I basically want the equivalent of "chkdsk /r" for ext3. 

If anyone can point to any good guides to learn the ins and outs, then that would be much appreciated! Thanks!

---

### Post by iball on 2006-11-10
fsck is used to check the file system for consistency.  Each file needs to have a parent, etc.  AFAIK, fsck is not used to check for bad sectors, etc.

Most drives are SMART - use smartctl to get the health status of your disk drives.

Something like:
```
sudo smartctl --all /dev/hda
```

You can do self tests using:
```
sudo smartctl --all /dev/hda -t short
```

What makes you think you may have bad sectors anyway?  Just make sure you make good backups of all your important files regularly, and you won't have any problems.

I hope this helps
--Ian

---

### Post by btboudreaux on 2006-11-10
> **iball said:**
> fsck is used to check the file system for consistency.  Each file needs to have a parent, etc.  AFAIK, fsck is not used to check for bad sectors, etc.

Most drives are SMART - use smartctl to get the health status of your disk drives.

Something like:
```
sudo smartctl --all /dev/hda
```

You can do self tests using:
```
sudo smartctl --all /dev/hda -t short
```

What makes you think you may have bad sectors anyway?  Just make sure you make good backups of all your important files regularly, and you won't have any problems.

I hope this helps
--Ian

Thanks, yes it does help and explains some things. I tried smartctl, but I don't seem to have that command. Is there something I need to install? I searched synaptic but didn't find anything. 

I do have another drive thats a backup drive. While making a backup one day, all my files weren't verified because my backup developed a bad sector. It's fine now and it hasn't spread but I like to check the disks I have every couple months just to make sure.

---

### Post by btboudreaux on 2006-11-10
Wait, I see smartmontools. Thanks again!

---

### Post by iball on 2006-11-10
Yep, I think smartmontools is what you want

--Ian

---

