---
title: "How can I synchronize FSCK?"
date: 2008-01-23
forum: General Help
---

### Post by Arenlor on 2008-01-23
I have two disks. One checks every 29 times the other every 27 times, and now they're quite off from each other. I wish to synch them up to run every 25 times and at the same time. I run without a bootsplash so I do happen to pay attention to them when they say * times until next fsck so time won't be a problem for me.

---

### Post by burbankmarc on 2008-01-23
Try changing both to boot up every time your computer starts.

```
sudo tune2fs -c 1 /dev/hda1 && sudo tune2fs -c 1 /dev/hda2

```

Then restart and they'll both be checked, then just change the count to 25, or whatever you want.

---

### Post by burbankmarc on 2008-01-23
sorry, i'm kind of retarded. 

You can set the last time the filesystem was checked with:

```
tune2fs -T YYYYMMDD /dev/hda1 && tune2fs -T YYYYMMDD /dev/hda2
```

now just change the count to whatever you want, say 25, and they'll now be sync'd

---

