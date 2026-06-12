---
title: "Cannot format  USB memory stick (opened read-only)"
date: 2022-01-03
forum: General Help
---

### Post by rbscebu on 2022-01-03
Ubuntu 20.04 and trying to format a 64GB SanDisk.

I plug in the memory stick, dismount it and open "Disks". The memory stick is listed as:[INDENT]
Size 63GB
Device /dev/sdc1 (Read-Only)
Contents Unallocated Space
[/INDENT]

When I try to go and format this memory stick in Disks, the Format command is greyed out. I am assuming that this is because /dev/sdc1 is read-only.

I have also tried to format this memory stick using GParted. The formatting command does not proceed stating "Cannot write to /dev/sdc, because it is opened read-only."

I do not need to save anything that is already on this memory stick. How can I format this USB memory stick?

---

### Post by HermanAB on 2022-01-03
to make a new filesystem, you need to unmount the schtick first.

---

### Post by rbscebu on 2022-01-03
> **HermanAB said:**
> to make a new filesystem, you need to unmount the schtick first.

Sorry, I should have mentioned this in the OP. I have tried formatting the memory stick while mounted and also unmounted. Same results either way. When trying with GParted, the memory stick cannot be mounted.

Disks shows the stick as Partitioning = Master Boot Record and the free space is 63GB.

---

### Post by ajgreeny on 2022-01-03
For what purpose was the stick last used?

If it was used to install a Linux .iso image you may need to create a new partition table first, most easily done from the Device menu of gparted.

---

### Post by sudodus on 2022-01-03
You can analyze the problems with your USB stick according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035) and if you are lucky, find a solution.

---

### Post by ActionParsnip on 2022-01-03
What filesystem are you using on the USB stick?

---

### Post by GhX6GZMB on 2022-01-03
Did you move the mechanical switch on the stick away from "write protect"?
That usually helps.

---

