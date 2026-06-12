---
title: "Encrytped USB disk not automounted"
date: 2007-06-14
forum: General Help
---

### Post by Matthai on 2007-06-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/120387](https://bugs.launchpad.net/bugs/120387) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have encrypted USB disk. It has been rewritten with random data, then created partition table and formatted with ext3:
sudo luksformat -t ext3 /dev/sdc1

Then I remove USB key and connect it againg - but it is not automounted.
However - I have another USB encrypted disk and is mounted normally without any problem.

When I say:
sudo mount -a

I get:
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/3234D4E934D4B159 ()

However - I can mount this device (/dev/mapper/luks_crypto_...) into
/mnt normally and it works perfect.

Please note that the second disk (which is automounted normally on my office machine) cannot be automounted in my home machine (I have to mount it manually).
I am using Ubuntu 7.04 with all updates (now kernel 2.6.20-16).

Any idea?


P. S. See the launchpad bug [https://bugs.launchpad.net/bugs/120387](https://bugs.launchpad.net/bugs/120387) for additional details.

---

