---
title: "MDADM External Bitmap at Boot"
date: 2013-12-03
forum: General Help
---

### Post by downingaustin on 2013-12-03
I would like to add a external Bitmap on my SSD. Although it works perfectly once I reboot it disappears from the out of **cat /proc/mdstat**.

I have tried adding **bitmap=/bitmap/bitmapMD1.bin** both array sections of my **/etc/mdadm/mdadm.conf** but it does not apply when my system boots. Here are the relevenant sections of my [B]/etc/mdadm/mdadm.conf.
[/B]
```
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=ccd5ab7a:582652ce:63ece3f3:716bb262 name=VeeamBackup:0
ARRAY /dev/md/1 metadata=1.2 UUID=e7bab8c4:cbe16f11:5824d398:34c9624b name=VeeamBackup:1


# This file was auto-generated on Wed, 27 Nov 2013 08:59:38 -0500
# by mkconf $Id$
DEVICE /dev/sdb /dev/sdd /dev/sde /dev/sdg /dev/sda
ARRAY /dev/md0 level=raid10 devices=/dev/sdb,/dev/sdd,/dev/sde,/dev/sdg,/dev/sda
DEVICE /dev/sdc /dev/sdf /dev/sdh /dev/sdi /dev/sdj /dev/sdk /dev/sdl
ARRAY /dev/md1 level=raid6 devices=/dev/sdc,/dev/sdf,/dev/sdh,/dev/sdi,/dev/sdj,/dev/sdk,/dev/sdl



```

What am I doing wrong?

---

