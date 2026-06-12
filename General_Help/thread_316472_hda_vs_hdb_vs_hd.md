---
title: "hda vs hdb vs hd*"
date: 2006-12-10
forum: General Help
---

### Post by shawnzyoo on 2006-12-10
So I got into an argument with a buddy over the following:
I originally inserted a hard drive into my system and it was labeled hda, what i hadn't notice was that it was on the master pin setting
now when i switched the pin to the slave setting and rebooted it showed it as hdb
are the two related? or completely unrelated and just a coincedence?
how does the file system see the different pin selections (if it sees it at all)?
Thanks

---

### Post by DaveBorealis on 2006-12-10
> **shawnzyoo said:**
> 
I originally inserted a hard drive into my system and it was labeled hda, what i hadn't notice was that it was on the master pin setting
now when i switched the pin to the slave setting and rebooted it showed it as hdb

That's the way it has always worked for me.  The master drive is hda, and the slave is hdb.  There are ways to change this, I'm sure, either in the bios or by mapping in grub.

Best regards,
Dave

---

### Post by aysiu on 2006-12-10
/dev/hda is going to be the first hard drive
/dev/hdb will be the second

It goes in alphabetical order.

---

