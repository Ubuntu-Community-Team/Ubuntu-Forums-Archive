---
title: "looking for an answer"
date: 2008-01-13
forum: General Help
---

### Post by trig on 2008-01-13
The test of the file system with type ext3 in partition #1 of SCSI1 (0,0,0) (sda) found uncorrected errors.

 any ideas guys and gals
trig

---

### Post by geraldm on 2008-01-14
It is time to run the filesystem check.  Read the manpage first.
```

sudo fsck.ext3 {device_name}

```
fsck.ext2 would also apply the journal.
Edit: I forgot the device after fsck.  Good thing I mentioned to look at the manpage. 
 
Gerald

---

