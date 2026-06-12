---
title: "suspend: resume not working (acpi ... interrupt...)"
date: 2005-04-20
forum: General Help
---

### Post by spotlight2001 on 2005-04-20
hi,

i tried software suspend. On both, to ram and to disk , resume doesnt work. It boots and halts: 
```

Linu
Radeon 9600 Pro Hynix B81533.09200
ACPI:PCI Interrupt 0000:00:1F.1[A]->GSI 18 (level,low) -> Irq 18
ACPI:PCI Interrupt 0000:02:05.1[A]->GSI 22 (level,low) -> Irq 22
ACPI:PCI Interrupt 0000:02:0c.1[A]->GSI 20 (level,low) -> Irq 20
ACPI:PCI Interrupt 0000:02:0c.1[B]->GSI 21 (level,low) -> Irq 21

```

I used this howto:
[http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM)

kernel: 2.6.10-5-686 (ubuntu binary kernel)

videocard: ATI (i read about problem with ati + suspend)
have this package installed
xorg-driver-fglrx
xorg-common
xserver-org

what could I try next to get suspend working ...
btw. I dont care about 3D - playing no longer - so if a solution contains using some old 2D driver or so ... I'll be happy as long suspend works

desktop
mainboard: asus p5p800 (s3 + s5 (ram+disks) work on winxp (huh the bad word)

in "/etc/X11/xorg.conf":
driver is "ati" NOT "fglrx" since fglrx doesnt work like described in tutorial:
busID = PCI:1:0:0 (although its an AGP, but i assume this is correct)
-> no manual changes by me here
[http://ubuntulinux.org/wiki/BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto)

Does anyone has suggestions which manual or howto I could try next? ... or is suspend due to ati problems out of question for me? Any help appreciated.

---

