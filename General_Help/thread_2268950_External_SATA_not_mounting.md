---
title: "External SATA not mounting?"
date: 2015-03-12
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-03-12
[COLOR="#FF0000"]On changing the eSATA cable and a reboot the problem has resolved itself.[/COLOR]


I use 14.04 LTS. I use/run Ubuntu's default: "Backup". It is set to automatically backup /home every Thursday. Today, the external SATA device will not mount. The eSATA is deliberately not in /etc/fstab. That is to prevent the 14.04 from treating it as "/" during powerup. I had to get help about that some years ago (12.04?). 

Typically, every Thursday, sometime during the OS's session, a panel indicator pops onscreen and reminds that the weekly backup will start when the device becomes available. That is when I power the eSATA up. 

I see errors, repeated in three logs, q.v., below:

dmesg

```
[   26.384248] ata1: SATA link down (SStatus 1 SControl 10)
[   26.384261] ata1: EH complete
[   26.392295] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen
[   26.392301] ata1: irq_stat 0x00800080, device exchanged
[   26.392308] ata1: limiting SATA link speed to 1.5 Gbps
[   26.392312] ata1: hard resetting link
```

and in kern.log

```

Mar 12 11:17:37 Lexington kernel: [ 1093.490166] ata1: SATA link down (SStatus 1 SControl 10)
Mar 12 11:17:37 Lexington kernel: [ 1093.490177] ata1: EH complete
Mar 12 11:17:37 Lexington kernel: [ 1093.497092] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen
Mar 12 11:17:37 Lexington kernel: [ 1093.497097] ata1: irq_stat 0x00800080, device exchanged
Mar 12 11:17:37 Lexington kernel: [ 1093.497103] ata1: limiting SATA link speed to 1.5 Gbps
Mar 12 11:17:37 Lexington kernel: [ 1093.497106] ata1: hard resetting link
```

and in syslog

```
Mar 12 11:19:24 Lexington kernel: [ 1200.622917] ata1: SATA link down (SStatus 1 SControl 10)
Mar 12 11:19:24 Lexington kernel: [ 1200.622928] ata1: EH complete
Mar 12 11:19:24 Lexington kernel: [ 1200.632990] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen
Mar 12 11:19:24 Lexington kernel: [ 1200.632995] ata1: irq_stat 0x00800080, device exchanged
Mar 12 11:19:24 Lexington kernel: [ 1200.633002] ata1: limiting SATA link speed to 1.5 Gbps
Mar 12 11:19:24 Lexington kernel: [ 1200.633005] ata1: hard resetting link
```

lspci shows:

```
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
. . . 
03:00.0 SATA controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
```

So I know the external (eSATA) card is on the pci-e bus. Powering up the eSATA drive should cause the device to mount itself and the "Backup" software to run, but that's not happening. Not today.

I did get a panel "Update Manager" red error icon this morning. It asked me to run the apt-get to attempt at fixing a problem. On calling the Update Manager, and clicking "Install all upgrades" the OS got a new Kernel, Image, and one component (dependency?) on Wine. The red panel icon mentioned a Wine dependency. After the reboot the red panel error icon was gone.

I've used Ubuntu for 6 years now, but am a novice when it comes to this kind of problem. I'm not afraid of the CLI, but am most a "cut and paster".

---

