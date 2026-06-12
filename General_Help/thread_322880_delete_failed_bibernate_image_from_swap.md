---
title: "delete failed bibernate image from swap"
date: 2006-12-21
forum: General Help
---

### Post by frogotronic on 2006-12-21
If hibernate has failed - how do I "delete" the failed hibernate image from my swap?

---

### Post by x64Jimbo on 2006-12-21
sudo dd if=/dev/zero of=<swap partition>

---

### Post by yopnono on 2006-12-21
Can't you just use sudo swapoff -a and sudo swapon -a

---

### Post by frogotronic on 2006-12-21
okay...

trying:

```
sudo dd if=/dev/zero of=/dev/hda5
```


EDIT:

Here's the output

```
sudo dd if=/dev/zero of=/dev/hda5
dd: writing to `/dev/hda5': Input/output error
3020153+0 records in
3020152+0 records out
1546317824 bytes (1.5 GB) copied, 379.547 seconds, 4.1 MB/s
```

Now...the System>Disks shows that the swap partition is there, but that there is no free space.

How do I remedy this?

-CH

---

### Post by frogotronic on 2006-12-21
```
sudo mkswap /dev/hda5
swapon -a
```


-CH

---

