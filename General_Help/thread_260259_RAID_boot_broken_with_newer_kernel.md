---
title: "RAID boot broken with newer kernel"
date: 2006-09-18
forum: General Help
---

### Post by HAARP on 2006-09-18
Sooo.
Basicly, using kernel **linux-image-2.6.15-26-k7** works fine. When booting, the first message I get is **mdadm started with...**. Now there's this **linux-image-2.6.15-27-k7** I would like to boot. However, I don't get **mdadm's** message. No RAID - no boot for me. How do I get RAID support into this newer kernel?

---

### Post by HAARP on 2006-09-18
Took me quite some time to figure this out...there's nothing about it to be found anywhere on the net.

```
sudo update-initramfs -u -k 2.6.15-27-k7
```

this did the trick for me. That information should probably be saved somewhere...

---

