---
title: "Errors on bootup"
date: 2019-07-18
forum: General Help
---

### Post by n4pl on 2019-07-18
hi,

im relativ new to Ubuntu Server (18.04) and its a fresh install (full wiped NVME with 1 HDD). Everything works fine but after every reboot i got 3 Errors in my log, i cant recognize any problems but a fix would be nice for this:

```

11:39 overlayfs: missing 'lowerdir' kernel
11:39 aufs aufs_fill_super:912:mount[1542]: no arg kernel
11:39 Couldn't get size: 0x800000000000000e kernel

```

yesterday i had an additional error:

```

13:57 MODSIGN: Couldn't get UEFI db list

```

this one got fixed bei enabling Secure Boot in my BIOS. Any ideas how to fix the other errors? Google wasnt my best friend to this issues.

Thanks

---

### Post by TheFu on 2019-07-18
aufs isn't used by many.  I'd ask that specific project ... or use LVM.  Can't say I've ever seen it used on a "Server" install, but we all have limited experience, even in 25+ yrs.

---

### Post by n4pl on 2019-07-18
> **TheFu said:**
> aufs isn't used by many.  I'd ask that specific project ... or use LVM.  Can't say I've ever seen it used on a "Server" install, but we all have limited experience, even in 25+ yrs.

i dont need?/want this aufs... so my question is how can i fix this? i only installed via USB Ubuntu Server 18.04 on my nvme and got this "aufs" error?!

---

### Post by TheFu on 2019-07-18
There are lots of messages in dmesg that are informational, not errors.

---

