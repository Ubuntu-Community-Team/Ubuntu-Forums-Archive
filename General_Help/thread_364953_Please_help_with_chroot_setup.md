---
title: "Please help with chroot setup"
date: 2007-02-18
forum: General Help
---

### Post by gollybegully on 2007-02-18
I'm trying to setup the dchroot command

what does this mean?
chris@chris-desktop:~$ dchroot
E: /etc/dchroot.conf: [edgy/chroot] location: line 1 [edgy/chroot]: Required key ‘location’ is missing

---

### Post by llamakc on 2007-02-18
> **gollybegully said:**
> I'm trying to setup the dchroot command

what does this mean?
chris@chris-desktop:~$ dchroot
E: /etc/dchroot.conf: [edgy/chroot] location: line 1 [edgy/chroot]: Required key ‘location’ is missing

I am unfamiliar with "dchroot" but the chroot command normally requires a place to pivot to, a directory for you to 'chroot' too. If dchroot is different, the error is clearly telling you that something is incorrect with your conf file in /etc/

---

