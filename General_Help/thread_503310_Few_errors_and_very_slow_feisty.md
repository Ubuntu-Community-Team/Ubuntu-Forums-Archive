---
title: "Few errors and very slow feisty"
date: 2007-07-17
forum: General Help
---

### Post by super.rad on 2007-07-17
I've had ubuntu for a while now, managed to sort out most problems but since i updated to feisty it has been much slower and whilst doing certain things it becomes so slow it's unusable. i've noticed in the system log there is a few errors that come up constantly, they are:

```
Jul 17 23:24:35 jimin-ubuntu kernel: [  320.988000] hdd: dma_intr: bad DMA status (dma_stat=76)
```
```
Jul 17 23:24:35 jimin-ubuntu kernel: [  320.988000] hdd: dma_intr: status=0x50 { DriveReady SeekComplete }
```
```
Jul 17 23:24:35 jimin-ubuntu kernel: [  320.988000] ide: failed opcode was: unknown
```
```
Jul 17 19:13:23 jimin-ubuntu kernel: [249583.568000] APIC error on CPU0: 40(40)
```

whenever i boot up i get the message:

MP-BIOS bug: 8254 timer not connected to IO-APIC

If anyone can help me solve any/all these problems it would be much appriciated. Thanks

EDIT: Also forgot to mention that im also unable to play dvd's. They play but they are really jumpy and completely unwatchable. I've followed all guides to get dvd playback but nothing works.

---

### Post by super.rad on 2007-09-18
It's still doing it, does anyone have any ideas?

---

### Post by splintercellguy on 2007-09-18
For the APIC issue try booting with noapic, other than that no idea.

---

### Post by super.rad on 2007-09-18
Thanks i've added the noapic option to my grub/menu.lst
Just noticed aswell i keep getting this message in the terminal
```
Fontconfig error: "~/.fonts.conf", line 2: no element found
```

---

### Post by super.rad on 2007-09-23
I was given another hard drive today and have re-installed kubuntu feisty on it and im now using a new IDE cable but its still just as bad so im guessing the problem must be the motherboard. Anyone have any ideas?

---

### Post by super.rad on 2007-10-16
Anyone?

---

