---
title: "Bad disk - how to force a fsck?"
date: 2006-11-21
forum: General Help
---

### Post by tenjin on 2006-11-21
Hi,

I just bought and installed a new 160Gb HDD and installed Edgy on it.

Everything was working fine for a day or so and then the drive started throwing lost of "IDE" and "SEEK ERROR" messages in the log, my VAR parition went bad and wouldn't mount, and the machine kept freezing. The drive also intermittantly emits a very loud series of knocking noises, kind of like banging your hard knuckles on a desk.

I'm assuming that the drive has failed, but is there a way to force a fsck so that it can at least have a try at fixing the problems?

Cheers

D.

---

### Post by wongdai on 2006-11-21
THis might do the trick for you:

sudo shutdown -F -h

Should force a fsck when you next startup.

---

