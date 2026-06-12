---
title: "How do you get drives to mount on boot?"
date: 2007-09-08
forum: General Help
---

### Post by Sir_Sid on 2007-09-08
Hi, I wrote the following two codes into the fstab but my two external drives will not mount on startup. Is there something I am doing wrong??

```
/dev/sdb1	/media/Mybook	vfat	defaults,unmask=222,noauto,users 0 0

/dev/sbc1	/media/500g ntfs-3g	defaults,unmask=222,noauto,users 0 0
```

---

### Post by merlinus on 2007-09-08
Check settings in System/Preferences/Removable Drives and Media.

-merlin

---

### Post by tripokey on 2007-09-08
Whats wrong with your config file is probably that you typed unmask instead of umask.

---

### Post by Sir_Sid on 2007-09-08
Ahh nice catch there, thank you

Well now my fat32 drive mounts on boot, but my ntfs drive still does not.

UPDATE

Ops, found another spelling mistake, it was sdc not sbc. Thanks for your help again :D

---

### Post by merlinus on 2007-09-08
You might try removing

noauto

-merlin

---

### Post by strabes on 2007-09-08
You should also use UUIDs instead of device locations.

---

### Post by little_penguin on 2007-09-08
> **Sir_Sid said:**
> Hi, I wrote the following two codes into the fstab but my two external drives will not mount on startup. Is there something I am doing wrong??

```
/dev/sdb1	/media/Mybook	vfat	defaults,unmask=222,noauto,users 0 0

/dev/sbc1	/media/500g ntfs-3g	defaults,unmask=222,noauto,users 0 0
```
I think there's typo in your ntfs path, which is probably why it's not mounting - I believe it's not /dev/s**b**c1, but should be /dev/s**d**c1 or similar

---

### Post by Sir_Sid on 2007-09-08
yes, I found all those
Thank you :)

---

