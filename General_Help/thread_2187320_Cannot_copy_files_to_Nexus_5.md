---
title: "Cannot copy files to Nexus 5"
date: 2013-11-11
forum: General Help
---

### Post by x-shaney-x on 2013-11-11
Trying to copy about 1GB of files from my hard drive to my Nexus 5 via Nautilus.
Firstly it is painfully slow progress and after over 2 hours it was well under halfway done.
Secondly certain files/folders keep failing with this error: ```
libmtp error: Could not send object info
```

I also had exactly the same problem copying files to my Nexus 4 before that.

---

### Post by TheFu on 2013-11-11
I had to load a PPA version to get my N4 device recognized at all under 12.04.  Which Ubuntu and do any files get copied?
Encryption on the device? Does it lock before finished?

---

### Post by x-shaney-x on 2013-11-11
Ubuntu 13.10, no encryption and no doesn't lock.
Some files do get copied other don't but even having problems with the ones that do copy.
For example, a few photos. videos and some other bits and bobs appear to have copied and appear on the Nexus according to Nautilus but when I look on the Nexus itself they aren't there.

---

### Post by TheFu on 2013-11-11
Have you tried a different machine, USB port, USB cable?

On my box, I have issues with long copies ... but it appears to be related to any copy over about 10 minutes.  If I split up the rsync, all is fine.

Is there anything useful in the logfiles?

BTW, I really hate that there isn't another SD memory slot on my Nexus - something that wouldn't need to use the MTP crap.

---

### Post by x-shaney-x on 2013-11-11
Tried different ports and cables, not another computer as the only other one to hand is a chromebook.

Thanks anyway, I was hoping there might be a known issue with an easy workaround.
I just can't be bothered troubleshooting things with ubuntu anymore, always seems to let me down when I actually need it so I will find some other way.

---

