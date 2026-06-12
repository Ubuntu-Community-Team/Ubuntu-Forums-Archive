---
title: "Mounting a partition from Live CD [Resolved]"
date: 2006-12-01
forum: General Help
---

### Post by shironeko on 2006-12-01
Well, I want to boot up the live CD and there mount a partition to an ubuntu partition I have on the Hard Drive.

Read and Write Please.

Thank you very much!

---

### Post by aysiu on 2006-12-01
Do you know what partition it is? Let's assume it's /dev/hda1 for now. If you don't know what it is, we'll tackle that later.

Put these commands into the terminal: ```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/hda1 /media/recovery
gksudo nautilus
```

---

### Post by shironeko on 2006-12-01
Ehm, yes I know what it Is, :P
Sorry, maybe I mixed up some words.
I meant that I wanted to mount an Ext3 Ubuntu partition I have.

Thanks!

---

### Post by aysiu on 2006-12-01
Those are the instructions for mounting the Ext3 Ubuntu partition you have.

I meant do you know if it's /dev/hda1 or /dev/hda5 or /dev/sda2...?

---

### Post by aidanr on 2006-12-01
"fdisk -l" will list your partitions, replace hda1 with whichever partition you installed ubuntu to

---

### Post by shironeko on 2006-12-01
Yeah, well, it was HDA2, but I figured it out, since hda1 is Windows.

THankyou very much!

---

