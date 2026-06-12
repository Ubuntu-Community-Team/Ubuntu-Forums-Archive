---
title: "dmraid memory corruption"
date: 2008-04-27
forum: General Help
---

### Post by paulis on 2008-04-27
I installed ubuntu 8.04 and then dmraid package to access data on my ntfs partition on raid.

But I have unexpected problems with dmraid - it produce memory corruption and exit.

For example:
paul@paulish:/mnt$ sudo dmraid -r
*** glibc detected *** dmraid: malloc(): memory corruption: 0x0806f740 ***

What can I do? How can I access ntfs partition on jmicron raid? How can I fix dmraid memory corruption?

---

### Post by Geertjanneman on 2008-06-15
hi paulis,

i cannot help you, but i can report having the same problem. mine outputs:

<quote>
ubuntu@ubuntu:~$ sudo dmraid -ay
*** glibc detected *** dmraid: malloc(): memory corruption: 0x0806f748 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e46356]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb7e47cad]
dmraid[0x8054ce7]
[...]
</quote>

i just booted the liveCD of Ubuntu 8.04 (ubuntu-desktop-i386) on my system, which is built from these parts:
- Gigabyte GA-P35-DS3 motherboard
- 4 x 1 GB RAM (dual channel)
- 2 x 500 GB Samsung Spinpoint T166 harddrive
  (these are connected to the JMicron (Gigaraid) SATA controller in RAID-0 configuration)
- Club3D Radeon 2600HD PCI-e videocard
- and some more parts which seem to be unimportant (so far)

please, if anyone out there has the same problem, please post your configuration here...

---

### Post by Geertjanneman on 2008-06-15
paulis, in case you didn't find it yet....


alrighty! anyone with the same problem, check this out:

[https://bugs.launchpad.net/ubuntu/hardy/+source/dmraid/+bug/221824](https://bugs.launchpad.net/ubuntu/hardy/+source/dmraid/+bug/221824)

The solution can be summarized as follows:

- in System->Administration->Software Sources, next to marking the "universe" repository, also mark "hardy-updates", which is under the "Updates"-tab
- then install dmraid package

(if it doesn't work after you were already messing around with the non-working dmraid, reboot your liveCD - because it won't uninstall properly - and reinstall dmraid as described above)

apparently it had something to do with the combination of dmraid and the JMicron controller

---

