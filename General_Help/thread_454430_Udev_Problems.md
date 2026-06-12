---
title: "Udev Problems"
date: 2007-05-25
forum: General Help
---

### Post by muadib on 2007-05-25
Hello,
Since my upgrade to Feisty, I am having trouble with udev:
Specifically, I am getting messages such as these:
--
[45887.989000] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
[45887.989000] device-mapper: ioctl: error adding target to table
--
I currently boot my Ubuntu using a mini cd that has a kernel, initrd and the tools necessary to decrypt and boot my encrypted swap and root. This problem with udev has only started since my upgrade to feisty.

The kernel version that I am using is 2.6.18 with some patches that I needed to apply for my last laptop to be able to read sd cards.

Furthermore, if I don't kill udevd, it eats up my cpu ressources and spits out messages as described above.

Any advice would be appreciated.

Thanks,

Mathieu

---

### Post by muadib on 2007-06-05
I decrypted my root filesystem and went back to a Ubuntu kernel and the problem has gone away.

---

