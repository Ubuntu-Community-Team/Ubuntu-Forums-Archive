---
title: "fstab missing defaults options"
date: 2014-04-18
forum: General Help
---

### Post by jason58 on 2014-04-18
My partition looks like this in fstab:
```
UUID=b96601ba-7d51-4c5f-bfe2-63815708aabd /               ext4    noatime,acl,errors=remount-ro 0       1
```

I noticed that they're not the usual "defaults" in the options list. I'm just curious if that's something that should be added, or if it's at times left out.

Purely an educational question. :)

---

### Post by steeldriver on 2014-04-18
I can't actually find a credible reference for this, but I think it's just (in the words of the Undertones) a case of "The chocolate's only there / to keep it the right length" i.e. the [FONT=courier new]defaults [/FONT]keyword is only required if you are not specifying any actual non-default mount options in the 4th field of the file (fs_mntopts), but *are *specifying a non-default value for the following field(s). Otherwise the mount/mountall command doesn't know which is which.

I think that people sometimes just choose to leave the [FONT=courier new]defaults [/FONT]keyword in so that if they ever remove all other options, the formatting of the file doesn't break.

---

