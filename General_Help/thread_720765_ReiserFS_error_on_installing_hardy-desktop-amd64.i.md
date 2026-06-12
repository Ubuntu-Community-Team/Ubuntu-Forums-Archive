---
title: "ReiserFS error on installing hardy-desktop-amd64.iso"
date: 2008-03-10
forum: General Help
---

### Post by mradev on 2008-03-10
When I choose the second not-empty SATA disk as an "installation drive"  just after the initial restart (verbose on) I get the following "error":

```

[36.301054] ReiserFS: sdb1: warning: sh-462: bad transaction max size (209220240). FSCK?


BusyBox etc...

(initramfs)_

```

If I choose the second partition on my first SATA disk everything's fine and dandy. BTW I observed almost the same behaviour (I can't remember the exact error message) with 7.04.04 and exactly the same behaviour  with alpha-5.

---

### Post by ago on 2008-03-10
not sure, I'll need the exact error msg, some more info on your disk setup. Also did you try running fsck|

---

### Post by mradev on 2008-03-10
> **ago said:**
> not sure, I'll need the exact error msg, some more info on your disk setup. Also did you try running fsck|

This is the exact error message.
What kind of fsck you suggest I should run? I believe there is no fsck as part of the BusyBox.

Attached more info about the storage subsystem.

---

### Post by ago on 2008-03-11
Do you have a resierfs partition at all?

---

### Post by mradev on 2008-03-11
Of course not - you could easily see that from the "report" file I've attached.

---

