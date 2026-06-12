---
title: "LiveCD help needed - squashfs and drive mounting"
date: 2007-10-15
forum: General Help
---

### Post by picopir8 on 2007-10-15
I have tweaked the LiveCD to contain the programs that I need and have put it on a USB stick so I can boot it from any computer that supprots USB boot.  However, I have a couple issues that I need help resolving before I can use this as an alternative to carrying around my laptop.

1) squashfs takes a bit long to uncompress.  I have more than enough room on my flash card so  I would prefer to keep the file system uncompressed.  I never tweaked the file system settings before so can someone tell me what needs to be changed or point me to a good tutorial.

2) There are a few scripts that I always want access to and do not want to put them on the persistent partition where they could be inadvertently deleted.  Consequently I would like to keep them on a read only partition and then mount them at boot.  If #1 is resolved I guess I can just create a directory in root and store the scripts there.  Otherwise is there an easy way to mount another partition that does not involve extracting the file system to make the change?

Thanks

---

