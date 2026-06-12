---
title: "Start Live CD with qemu"
date: 2004-12-12
forum: General Help
---

### Post by Leonida on 2004-12-12
As Live CD ppc is not supplied, I wish start x86 Live Cd with qemu.
I know that Live Cd works fine with Virtual PC.
I run qemu 0.6.0 on iBook G4 933 OSX 10.3.6 with this command:
```
~ qemu -cdrom warty-release-live-i386.iso -m 164 -boot d
```But qemu window quit after a while giving me this error:```
QEMU 0.6.0 monitor - type 'help' for more information
(qemu) Segmentation fault
```
I also tried other GRUB options like "Filesafe mode" or "Expert mode" and all the "More boot options" without succes.

Thank .L.

---

