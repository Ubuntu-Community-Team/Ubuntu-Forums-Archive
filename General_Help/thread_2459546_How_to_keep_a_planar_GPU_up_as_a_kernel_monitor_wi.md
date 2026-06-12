---
title: "How to keep a planar GPU up as a kernel monitor with X on an add-in?"
date: 2021-03-21
forum: General Help
---

### Post by bcschmerker on 2021-03-21
**I've a situation with the *e*machines®/ac*e*r® EL1210-09 that I'm preparing for projector duty:**  X.org wanted to hijack the planar nVIDIA® C77 rev. a2 (Tesla: *geForce*® 8200 / *nForce*® 780a SLI) for GNOME Display Manager when I already have an *msi*® N610GT-1GD3-LP (nVIDIA® GF119 rev. a1 - Fermi: GeFORCE® GT&#8482; 610) for the purpose and the proper nvidia-390 (Fermi and later) support software installed.  This problem I partially solved with a custom-crafted Xorg.conf file that assigns the VESA non-accelerated video driver to the C77 and the nvidia-390 driver to the GF119, going verbose with BusID.  However, I intend to keep the C77 up for a kernel monitor, consistently with remote serial display units, rather than have it black out when X is online.
```
...
# 02:00.0 VGA compatible controller [300]: NVIDIA Corporation C77 [geForce 8200] [10de:084b], rev. a2
Section "Device"
	Identifier	"VideoAdapter0"
	Driver		"vesa"
	BusID		"PCI:2:0:0"
	VendorName	"Acer Computer Inc."
	BoardName	"DAO78L Boxer"       
	...
EndSection

# 03:00.0 VGA compatible controller [300]: NVIDIA Corporation GF119 [GeForce GT 610] [10de:104a], rev. a1
Section "Device"
	Identifier	"VideoAdapter1"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	VendorName	"Micro Star International"
	BoardName	"N610GT-1GD3-LP"
	...
EndSection
...
```Is there a different Driver handle I should have used on Card 0; or should I look elsewhere for the "serial terminal" act for the C77?

---

