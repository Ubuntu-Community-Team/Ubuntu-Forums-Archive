---
title: "Cannot find my NTFS partition anymore"
date: 2007-12-12
forum: General Help
---

### Post by v604mustangjoe on 2007-12-12
so i used to have an icon on my desktop titled hda1 that would allow me to get to my windows xp NTFS partition, now its not there.... how do i get it back? I went into terminal and typed mount hda1 but it couldnt find it.

---

### Post by oeolycus on 2007-12-12
What does this command display:

```
sudo fdisk -l
```

---

### Post by v604mustangjoe on 2007-12-12
just gives you another command prompt after

---

### Post by oeolycus on 2007-12-12
Sorry, newb mistake.

```
sudo fdisk -l
```

---

### Post by Stormspireiv on 2007-12-12
My guess is the NTFS partition was last used by Windows and Windows was not shut down properly and/or the NTFS partition has errors.  Try installing ntfsfix (it's in the repositories) and running that on the NTFS partition.  Then, after running ntfsfix, boot into Windows (when windows is starting up, it should run chkdsk on that partition) and shut down properly. Your partition should mount properly in Linux now.

---

### Post by v604mustangjoe on 2007-12-13
does hibernating windows have anything to do with it?

---

### Post by kpkeerthi on 2007-12-13
> **v604mustangjoe said:**
> does hibernating windows have anything to do with it?

Yes. The partion will be marked 'in use' and ubuntu will have trouble mounting it.

---

