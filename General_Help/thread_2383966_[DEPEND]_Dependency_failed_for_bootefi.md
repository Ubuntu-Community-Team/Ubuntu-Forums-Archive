---
title: "[DEPEND] Dependency failed for /boot/efi"
date: 2018-01-31
forum: General Help
---

### Post by prodevguy on 2018-01-31
Hello,

I installed Windows 10 after installing ubuntu 17.10, and grub was not working. I then rebooted into a live cd, boot-repared with recomended settings, then reboot. When I tried to boot into Ubuntu, I get the following errors:

```

[COLOR=#333333][FONT=Ubuntu]10:39:07 kernel: Couldn't get size: 0x800000000000000e[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]10:39:07 kernel: MODSIGN: Couldn't get UEFI db list[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]10:39:07 kernel: Couldn't get size: 0x800000000000000e[/FONT][/COLOR]


[TIME] Timed out waiting for device dev-disk-by\x2duuid-BC29\x2d65FC.device
[DEPEND] Dependency failed for /boot/efi
[DEPEND] Dependency failed for Local File Systems
[DEPEND] Dependency failed for Clean up any mess left by Odns-up
[DEPEND] Dependency failed for File System Check on /dev/disk/by-uuid/BC29-65FC



```


Then Ubuntu goes into maintenance mode, which i am unsure what to do from their.

 I also tried running fsck, but it did not do anything.


Any ideas on how to fix?

Thank you.

---

### Post by ajgreeny on 2018-01-31
Which version of Ubuntu?

I get a similar error message showing on a virtual install of 18.04 in VirtualBox, but the OS boots and runs fine.
Can you boot to your install or does it freeze?

---

