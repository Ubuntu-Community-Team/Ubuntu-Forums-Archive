---
title: "Do I have a IRQ problem here?"
date: 2007-03-24
forum: General Help
---

### Post by jaripetteri on 2007-03-24
I  have AMD64 3200+ on Abit KN8 Ultra with GeForce 6600 PCI-e and it keep hanging sometimes. I have the lates BIOS and tryed nVidia drivers from repos and form nVidia site. It may keep up and running days or minutes until it freeze. 

Here is what I found on my dmesg:
```
jari@hobbes:~$ grep pcie /var/log/dmesg
[17179570.316000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.316000] Allocate Port Service[0000:00:0b.0:pcie00]
[17179570.316000] Allocate Port Service[0000:00:0b.0:pcie03]
[17179570.316000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.316000] Allocate Port Service[0000:00:0c.0:pcie00]
[17179570.316000] Allocate Port Service[0000:00:0c.0:pcie03]
[17179570.316000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.316000] Allocate Port Service[0000:00:0d.0:pcie00]
[17179570.316000] Allocate Port Service[0000:00:0d.0:pcie03]
[17179570.316000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.316000] Allocate Port Service[0000:00:0e.0:pcie00]
[17179570.316000] Allocate Port Service[0000:00:0e.0:pcie03]

```

So the invalid IRQ may be the reason but is there anything I can to about it?

[edit]almost forget. I'm using 2.6.17-11-generic kernel and also tryed 17-10's and 386's combinations.[/edit]

---

### Post by jaripetteri on 2007-03-25
I tried with Knoppix Live-CD and there I don't get those errors.

Same error on boot from 6.10 Live-CD.

anyone?

---

