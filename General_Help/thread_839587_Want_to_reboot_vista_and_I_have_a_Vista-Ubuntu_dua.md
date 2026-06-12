---
title: "Want to reboot vista and I have a Vista-Ubuntu dual boot"
date: 2008-06-24
forum: General Help
---

### Post by kronos444 on 2008-06-24
Hi everybody:)

I have a Vista-Ubuntu dual boot and recently I've been having trouble with Vista: some startup programs stop working,slower performance, etc.](*,)
I decided to reboot Vista, so I could have its original configuration back, which would overwrite my ubuntu partition, so I was afraid it would mess up with GRUB by doing so.(Also, I have a third partition with another version of ubuntu) So I was hoping if anyone could help me?

---

### Post by VMC on 2008-06-24
> **kronos444 said:**
> Hi everybody:)

I have a Vista-Ubuntu dual boot and recently I've been having trouble with Vista: some startup programs stop working,slower performance, etc.](*,)
I decided to reboot Vista, so I could have its original configuration back, which would overwrite my ubuntu partition, so I was afraid it would mess up with GRUB by doing so.(Also, I have a third partition with another version of ubuntu) So I was hoping if anyone could help me?

So how do you want it to look like when your through? Vista and which ubuntu? Or just Vista.

In either case show output of this command, from Terminal:

```
sudo fdisk -l
```

---

### Post by kronos444 on 2008-06-24
> **VMC said:**
> So how do you want it to look like when your through? Vista and which ubuntu? Or just Vista.

In either case show output of this command, from Terminal:

```
sudo fdisk -l
```

Hi, thanks for your answer.:)
I want it to have Vista only and later I'll install ubuntu 8.04 again.

Here's the command output (by the way, it's in Spanish):lolflag:

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x1460a25e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020        5394    35142187+   6  FAT16
/dev/sda3            5395        7374    15904350    7  HPFS/NTFS
/dev/sda4            7375        9730    18917376+   f  W95 Ext'd (LBA)
/dev/sda5            7375        8349     7825195+  83  Linux
/dev/sda6            8637        9730     8779776    7  HPFS/NTFS
/dev/sda7   *        8350        8615     2136613+  83  Linux
/dev/sda8            8616        8636      168651   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco


So I hope you can help me, and thanks for all your time

---

### Post by WRDN on 2008-06-24
If you reinstalled Vista, you should be able to install it on the partition its currently on, and it won't touch Ubuntu.
Also, after installing it, it will overwrite GRUB with its own bootloader, but you can [reinstall GRUB from the LiveC]("http://ubuntuforums.org/showthread.php?t=224351")D.

---

