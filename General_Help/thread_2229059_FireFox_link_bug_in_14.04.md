---
title: "FireFox link bug in 14.04"
date: 2014-06-11
forum: General Help
---

### Post by Macamba on 2014-06-11
I recently installed the latest version of Ubuntu. If I remember correctly it is 14.10 (3.13.0-29-generic). I noticed when I've been in FireFox, switched to other programs, and go back to FireFox I can not click links when my mouse is on the link. I only get the "hand" icon when my mouse is about a centimetre higher in the document. Is that a bug in Ubuntu?

---

### Post by Cavsfan on 2014-06-11
> **Macamba said:**
> I recently installed the latest version of Ubuntu. If I remember correctly it is 14.10 (3.13.0-29-generic). I noticed when I've been in FireFox, switched to other programs, and go back to FireFox I can not click links when my mouse is on the link. I only get the "hand" icon when my mouse is about a centimetre higher in the document. Is that a bug in Ubuntu?

Not sure about your problem with Firefox but the kernel for 14.10 Utopic is currently 3.15.0-5-generic:

```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.15.0-5-generic #10-Ubuntu SMP Mon Jun 2 17:00:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Cavsfan on 2014-06-11
It is Trusty 14.04 that uses the 3.13.0-29-generic kernel not Utopic 14.10.

[https://launchpad.net/ubuntu/trusty/+package/linux-image-3.13.0-29-generic](https://launchpad.net/ubuntu/trusty/+package/linux-image-3.13.0-29-generic)

---

### Post by Macamba on 2014-06-23
So. I had the wrong version.

> **Macamba said:**
> I recently installed the latest version of Ubuntu. If I remember correctly it is **14.04** (3.13.0-29-generic). I noticed when I've been in FireFox, switched to other programs, and go back to FireFox I can not click links when my mouse is on the link. I only get the "hand" icon when my mouse is about a centimetre higher in the document. Is that a bug in Ubuntu?

---

### Post by grahammechanical on 2014-06-23
It means you are in the wrong section of the forum. This section is for those of us running and testing the next version of Ubuntu during its 26 week development period.

The problem could mean that it is a bug in Firefox. But unless other users are having this problem it is difficult to identify it as a bug or as something strange that is happening only on your machine.

I do not have this when I switch between Chromium and Firefox. I am using Utopic Unicorn (14.10), Linux kernel 3.15.0.6-generic and Firefox 30.

Regards.

---

### Post by philinux on 2014-06-23
Moved to General Help and thread title amended.

---

