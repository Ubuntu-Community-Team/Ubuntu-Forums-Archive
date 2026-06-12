---
title: "problem with instalation"
date: 2020-07-03
forum: General Help
---

### Post by phrek on 2020-07-03
[ATTACH=CONFIG]286389[/ATTACH]

hi guys when im trying to install xubuntu i had this, what could be ? 

pls, i need your help with this!

---

### Post by pqwoerituytrueiwoq on 2020-07-04
output of [FONT=courier new]lspci[/FONT] please

---

### Post by phrek on 2020-07-04
hey! the only way to get there was by virtualbox
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: VMware SVGA II Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0b.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)

---

### Post by ajgreeny on 2020-07-04
The output from Virtualbox does not help as it shows a lot of the virtual hardware, not you hard-metal hardware.

I suspect from the image you attached that this is a graphics driver problem, so we really need the output from the running installer.
You may need to boot the USB using the nomodeset  boot option so try that first.
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for more info

---

### Post by phrek on 2020-07-04
[ATTACH=CONFIG]286391[/ATTACH]

Thx to reply, this is what i have

---

