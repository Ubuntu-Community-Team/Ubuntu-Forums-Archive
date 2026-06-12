---
title: "System freezes often"
date: 2013-01-05
forum: General Help
---

### Post by TrueTashtego on 2013-01-05
Hi.

After several minutes of working suddenly my system hangs.
Its Ubuntu 12.04 LTS with latest updates on a new computer with 8 core CPU and SSD hard disc. Can I find any further informations about why the system hangs in Unity and no STRG+ALT+F2 or anything else works anymore?

The only thing I could think of making trouble is the graphic card, because I cant install the "additional drivers", it shows me "AMD Unsupported hardware". Could that be a hint?

Thanks

---

### Post by jk3920 on 2013-01-05
What are your hardware specs? Have you tried LXDE?

---

### Post by 2F4U on 2013-01-05
There may be a hint to what the problem is in the system logs:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

The graphics card may be the root, however, graphics problems are usually experienced visually in the form of artifacts or glitches. Since this is a new machine, did you verify that the RAM is working ok? Defective RAM often accounts for random hangs or crashes. An easy way to rule out RAM is by running memtest from a liveCD.

---

### Post by TrueTashtego on 2013-01-05
Hi.

Thanks for the reply!

Specs:
Ubuntu: 12.04.1 LTS
Memory: DIMM 8 GB DDR3-1600 Kit
CPU: AMD FX 8120 8x
VGA: installed is VESA: PITCAIRN (said by "All Settings - "Details"), but its a Radeon HD 7850 Royal King
HDD: Premier Pro SP900 2,5" SSD 128 GB

No I didnt try LXDE, i definitely prefer Unity.

---

### Post by TrueTashtego on 2013-01-06
hi again.

the memtest didnt show up any problems. and i couldn´t see anything of interest in the syslogs. but i think i know the source of the problem. since some days i am developing an openGLES 2.0 game for android. and I am testing it sometimes live with my handy, other times with an android emulator device. when i am using the emulator, start may app, then switch to the browser and google something, after some minutes being "away from the emulator" it freezes my system. so I think its definitly related to open gl and my graphic card. :( but i cant install the correct drivers unfortunately! When running "Additional drivers" - "Active" on ATI/AMD proprietery FGLRX graphics driver, it says: 

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2013-01-06 10:56:05,216 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-01-06 10:56:36,293 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-06 10:56:36,293 DEBUG: fglrx_updates is not the alternative in use
2013-01-06 10:56:36,328 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-01-06 10:56:36,328 DEBUG: fglrx_updates is not the alternative in use

:(

---

### Post by dino99 on 2013-01-06
with very new hardware you should install and use the latest kernel to get better identification chance.

Into an empty folder, download the packages for your ubuntu (32 or 64 bits):
- the 2 headers (....all.deb, ....amd64.deb ; for 64 bits for example)
- the 2 images  ( image & image-extra)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

then, from that folder where you have downloaded the kernel packages, run:

sudo dpkg -i *

then reboot on that kernel (hold "shift" key down at bios end process to get the grub menu on a single OS system)

---

### Post by duranl on 2013-04-27
What ended up happening with this?  Did you get the video card to work properly?

---

