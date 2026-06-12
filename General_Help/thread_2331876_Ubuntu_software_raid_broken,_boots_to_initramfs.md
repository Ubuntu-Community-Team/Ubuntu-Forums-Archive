---
title: "Ubuntu software raid broken, boots to initramfs"
date: 2016-07-26
forum: General Help
---

### Post by redking3 on 2016-07-26
I have installed my os on two 120gb SSDs in ubuntu software raid 1, but somehow I have managed to break it, and need some help.
 
The disks are still both plugged in and I think they both still work, but before the last reboot on the ubuntu server I passed a disk through to a VM, and since I have the disk placement of a complete morron, I managed to passthrough the wrong disk witch happened to be one of the disks in my raid 1. I ofcourse removed the passthrough immidietly and hoped that the raid would fix itself again, but that dossent seem to have happened..

as it boots up it starts to wait for one of the drives, and after 30sec or so it says that one of the drives with a certain UUID is missing and boots in to ramfs. Now I realise that I could have prevented this issue beforehand by making it not boot in to ramfs incase of a broken or missing disk pretty easy by editing [COLOR=#333333][FONT=monospace]/etc/initramfs-tools/conf.d/mdadm[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]  and setting "[/FONT][/COLOR]BOOT_DEGRADED=true". But I didnt know this before I started reading after this happened :(

So I really need some help figuring out the steps on how to fix this so I can boot my OS again. I have newer been in initramfs before so dont really know how to fix the [COLOR=#333333][FONT=monospace]/etc/initramfs-tools/conf.d/mdadm file from here. is that possible?[/FONT][/COLOR]

---

