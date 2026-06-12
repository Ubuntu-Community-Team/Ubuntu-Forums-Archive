---
title: "External HD toast?"
date: 2021-04-07
forum: General Help
---

### Post by daanheuvelbeuk on 2021-04-07
During installation of my Ubuntu 20.04 I unplugged my external USB HD. Now my installation has succeeded I do not see the HD in either Ubuntu nor my other OS. Is it possible to access the data on the HD, or if not, to be able to use the HD?

FWIW, the HD is still shown during startup in my Bios, and the light of the HD is on.

---

### Post by tea for one on 2021-04-07
A bit more info required

Which file system(s) is(are) present on this external HD?
More than one partition?
Encryption or other security feature?
Do you need to recover the data?

Your other OS, what is it?

When you remove an external storage device in an unsafe manner, you can potentially damage the file system.
It is then sensible to use the appropriate tools to try and fix the file system, depending on the type of file system used.
For example, Windows tools for Windows file systems.

---

### Post by daanheuvelbeuk on 2021-04-07
> **tea for one said:**
> A bit more info required

Which file system(s) is(are) present on this external HD?
More than one partition?
Encryption or other security feature?
Do you need to recover the data?

Your other OS, what is it?

It is a Seagate usb HD, that came with a Windows format. It had only one partition. It was not encrypted. And yes I need to recover data, but I assume it is lost. I cannot access the data/HD from Windows either, but now know how to format the disk under Windows from a Seagate website. I will need to recover the data from the old HD. :’-)

Thanks for the help. I now see the data at least is toast, not so the hardware itself (fingers crossed).

---

### Post by dragonfly41 on 2021-04-07
Try running testdisk probably from Windows session if the HD was Windows.
Or other recovery tools.

---

### Post by TheFu on 2021-04-07
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
It probably isn't as grim, provided you are prepared for many, many, many, many, hours of manual effort.  Any files that have been overwritten, are gone. There could be 50 versions of all the other files as new versions were saved over time.  Which is the most recent?  Only someone intimately knowledgeable about the files would know.

For storage that is connected to Linux, a native linux file system is best for performance and posix permission support.  Access by other systems over the network is easier too.

---

