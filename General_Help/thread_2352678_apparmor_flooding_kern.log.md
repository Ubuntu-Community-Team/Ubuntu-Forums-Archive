---
title: "apparmor flooding kern.log"
date: 2017-02-14
forum: General Help
---

### Post by pksings2 on 2017-02-14
I started getting messages about apparmor denying samba functions. Samba seems to be running fine however.  Ran rootkit scan, nothing.  It's probably a bug, anybody know how to stop it?

Feb 14 09:24:26 phred kernel: [  923.700986] audit: type=1400 audit(1487093066.981:173): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/8892" pid=8892 comm="smbd" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701022] audit: type=1400 audit(1487093066.981:174): apparmor="ALLOWED" operation="truncate" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/8892" pid=8892 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701266] audit: type=1400 audit(1487093066.981:175): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/3324" pid=8892 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701400] audit: type=1400 audit(1487093066.981:176): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/3371" pid=8892 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701496] audit: type=1400 audit(1487093066.981:177): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/3369" pid=8892 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701619] audit: type=1400 audit(1487093066.981:178): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/3368" pid=8892 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701646] audit: type=1400 audit(1487093066.981:179): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/8291" pid=8892 comm="smbd" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
Feb 14 09:24:26 phred kernel: [  923.701859] audit: type=1400 audit(1487093066.981:180): apparmor="ALLOWED" operation="unlink" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/8892" pid=8892 comm="smbd" requested_mask="d" denied_mask="d" fsuid=0 ouid=0

---

### Post by &amp;KyT$0P# on 2017-02-14
Looks like your apparmor profile for Samba needs this line -
```
/run/samba/** rw,
```

> **pksings2 said:**
> I started getting messages about apparmor denying samba functions. Samba seems to be running fine however.
Samba runs fine because the apparmor profile is in complain mode.  Apparmor is not actually denying anything there, just logging violations.

---

### Post by oldos2er on 2017-02-14
Thread moved to *General Help*

---

