---
title: "Truecrypt Can't Save Files to Mount?"
date: 2008-01-30
forum: General Help
---

### Post by trmentry on 2008-01-30
I've been using truecrypt on Gutsy.  Downloaded the DEB from Truecrypt itself.  Its been working great.

Lastnight I mounted a volume I've been using and tried to move some files over to it.  I got the following error for them.

```

mv: cannot create regular file `/home/trmentry/mnt/tc/super-file.doc': No space left on device

```

 The files don't appear to be corrupt as I can open them and whatnot fine.   And yes, the truecrypt volume has space.... 89M free.  I tried both mounted as user and root.  Plus move as user and root.   No dice.   This just started.  The volume was working fine a day ago.   I tried making a new volume but get the same issues.

Has anyone else seen this?

Thanks

---

### Post by trmentry on 2008-01-30
Too add a bit of confusion to this... I was able to save the files I wanted to my volume by moving the directory they were in to the volume.  They moved fine then.  

But if I try and put them in the root, nada.  


Could this be a number of files in the directory thing?  The volume is a FAT filesystem.

---

