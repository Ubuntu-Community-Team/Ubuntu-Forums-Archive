---
title: "Not...good...  (GRUB/boot problem)"
date: 2008-04-26
forum: General Help
---

### Post by Lord Xeb on 2008-04-26
I was trying to resize my partition with Gparted (on the Ubuntu LiveCD), but I clicked cancel... I think that was a bad idea. When I went to boot, it will go through then go to a black screen with a flash cursor. When I go into recovery, it will get to the part that it checks the file system, then it will say 

```
checking Files Systems fsck 1.4.2
fsck.ext3 unable to resolve 'UUID=8ac63799-2a29-4668-90cd-1cf6fc3a6a8e'
[COLOR="Red"]fsck died with exit status 8[/COLOR]
```


I have looked all over for help and so far nothing has D:

Please help!

---

### Post by ryanhaigh on 2008-04-27
If you have resized the partiton the uuid (like a unique fingerprint for each partition) will have changed, to get this to work you will need to modify both grub and fstab to use the new uuid.

This may provide a starting point: [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/

---

