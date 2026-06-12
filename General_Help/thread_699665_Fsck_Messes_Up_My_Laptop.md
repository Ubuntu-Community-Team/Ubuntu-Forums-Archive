---
title: "Fsck Messes Up My Laptop??"
date: 2008-02-17
forum: General Help
---

### Post by adn258 on 2008-02-17
I have to reinstall ubuntu once before today it did it again at boot time nothing bad happen but it makes me nervous.  Is it really necessary that that needs to check it so often or even check it AT ALL?  Can i turn it off?  Can I make it not happens as often?  If so how?  Also is it crucial??

---

### Post by astrotech226 on 2008-02-17
I've had it hang my laptop during checks after the 38 mounts or whatever it's default is.  An easy way to disable the forced fsck during normal use is with tune2fs.  Assuming the partition that is giving you trouble is /dev/sda1, do this from the command line:

```
sudo tune2fs -i 0 -c 0 /dev/sda1
```

This sets the mount count to never and the number of days/weeks/months interval to never.

---

### Post by steveneddy on 2008-02-17
Sometimes I Fsck up my laptop, too.

---

### Post by adn258 on 2008-02-17
> **steveneddy said:**
> Sometimes I Fsck up my laptop, too.

yeah it seems like it messes up the computer lol like nothing bad happens until it starts it's thing.

---

