---
title: "Stop automounting of DVD/CD drives"
date: 2007-05-08
forum: General Help
---

### Post by Ledah on 2007-05-08
Hi, 

my CD's/DVD's were mounted automatically at every startup and if I put a new CD/DVD in the drive. But the fstab forbids aoutomount:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,**noauto**     0       0
```

I have this problem since Kubuntu Edgy 32Bit. Now I use Kubuntu Feisty 64Bit, but the problem is the same. Is this a bug or is there a new parameter to avoid automounting? Is there a way to stop it?

---

### Post by finer recliner on 2007-05-08
hmm im using ubuntu 6.06. i also have the noauto paramater, yet my cdrom is also mounted automatically at boot.

so yeah, i guess i have the same issue (is this an issue?)

---

### Post by bchaffin72 on 2007-05-08
I have solved this problem in Ubuntu 6.10. Go to the System menu. Select Preferences. Select removable Drives and Media, and under the Storage tab, uncheck the mount and browse options.

I don't know about Kubuntu, but the answer may be the same or similar.

---

### Post by Ledah on 2007-05-11
> **bchaffin72 said:**
> 
I don't know about Kubuntu, but the answer may be the same or similar.
Maybe, but unfortunately I don't find one :(

---

