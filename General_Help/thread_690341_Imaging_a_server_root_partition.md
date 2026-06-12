---
title: "Imaging a server root partition"
date: 2008-02-07
forum: General Help
---

### Post by rocktorrentz on 2008-02-07
I have a server which I can't really boot off a live cd in order to image the root partition for backup purposes. Is there a way I could get it to mount root read-only then make an image on the /home partition (RAID 5) on reboot or otherwise?

Thanks in advance

---

### Post by kidders on 2008-02-09
Hi there,

You *could* do that, I suppose, but booting another OS would be far easier. Depending on why you'd rather not use a LiveCD, there may be a better alternative.

---

### Post by rocktorrentz on 2008-02-09
The server is in my loft with no cd drive in it so it is pretty awkward to run a livecd. If I re-build it I might make a small secondary partition with just ssh so I can backup the main root partition.

---

