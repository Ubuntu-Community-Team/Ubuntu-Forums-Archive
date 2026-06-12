---
title: "Moving RAID 5 volume"
date: 2013-03-26
forum: General Help
---

### Post by ultrapain on 2013-03-26
I built a new server with a fresh install of Ubuntu Server 12.10 LTS x64.  I expected to be able to pick up the 3 2TB drives (RAID-5 volume via Ubuntu software RAID) I had in my old server and drop them in the new server.  The old server had the exact same o/s, just on different hardware.  During install I noticed a couple RAID packages being added by the installer.  During partition setup the installer even showed the 4TB RAID-5 volume being present.  The o/s installation went swimmingly.  After reboot I see the GRUB loader and I take the default selection of booting into the o/s, but it immediately goes to an initramfs prompt after spewing a bunch of information.  I tried to read the screen, but alas this system is quite fast thanks to the OCZ Synapse SSD boot drive.

While I have a good backup of the data, I would certainly prefer to keep the volume intact and simply mount it on the new server.  If you don't mind, can you give me some direction on where and how to begin troubleshooting this?  Thanks in advance for any help ~

Cheers!

---

### Post by ultrapain on 2013-03-31
[COLOR=#333333]I should apologize as my post didn't have the right release. The correct release was 12.04. Anyway, I was able to resolve the issue. My boot drive is so fast that I didn't notice a brief pause when initramfs was loading. I was being prompted because my array was degraded for some reason. I ignored the issue and booted successfully, then reassembled the array and added the "missing" drive back in using mdadm.[/COLOR]

---

