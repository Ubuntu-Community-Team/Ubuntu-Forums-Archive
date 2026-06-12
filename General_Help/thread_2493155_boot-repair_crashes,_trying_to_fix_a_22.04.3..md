---
title: "boot-repair crashes, trying to fix a 22.04.3."
date: 2023-12-05
forum: General Help
---

### Post by phdcam on 2023-12-05
After an unexpected crash (while running an ffmpeg transcode), my 22.04.3 LTS box won't boot:
"Kernel panic - not syncing: no working init found."

So I followed the instructions from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).
Despite setting the bios's uefi variables protection to disabled,
boot-repair fails, "Error: NVram is locked (Ubuntu not found in efibootmgr). Locked-NVram detected."

Pastebins from boot-repair, from oldest to newest:
[https://paste.ubuntu.com/p/WwtZp3pwJx/](https://paste.ubuntu.com/p/WwtZp3pwJx/)
[https://paste.ubuntu.com/p/Ww63pTwhcT/](https://paste.ubuntu.com/p/Ww63pTwhcT/)
[https://paste.ubuntu.com/p/4s9wyKbRY9/](https://paste.ubuntu.com/p/4s9wyKbRY9/)

The bios has no passwords set, nothing fancy.  The install is about a month old, default partitions, on a Tensor-I22 from [https://fit-iot.com/web/](https://fit-iot.com/web/).
How should I get it to boot again?
Can I use some bash# commands instead of this GUI tool, to isolate the problem?

---

### Post by oldfred on 2023-12-05
We are seeing a lot of Locked NVRAM issues.


Can you use Boot-Repair's advanced mode and choose to totally reinstall grub and choose to install latest kernel?
Be sure to boot in UEFI boot mode.

---

### Post by phdcam on 2023-12-06
To force the boot to be UEFI, I disabled CSM in the BIOS.  There, I also disabled Secure Boot.
Then in boot-repair I chose Advanced > Main > checkbox "reinstall grub",
Advanced > Grub options > checkbox "purge grub before reinstalling", and
Advanced > Grub options > checkbox "purge kernels then reinstall last kernel".
Now the internal disk boots cleanly.  Thank you!!
As expected, grub now offered only one version of the kernel, not four.

However, boot-repair still reported some problems that may interest you:

- "grub-install: warning: EFI variables cannot be set on this system. ... You will have to complete the GRUB setup manually."
- "NVram is locked (Ubuntu not found in efibootmgr)" remained.
- "'/sys/firmware/efi/vars': No such file or directory": instead, /sys/firmware/efi/efivars?
- "Module efivars not in /lib/modules/6.2.0-26-generic".
See [https://paste.ubuntu.com/p/pxNr7ZRzRt](https://paste.ubuntu.com/p/pxNr7ZRzRt).

---

### Post by oldfred on 2023-12-06
I have Kubuntu 22.04.3.
My kernels are -36 and -37 as current kernels, plus several older 5.15 versions.
Are you booting with -26 or also have newer kernels?

I do not have efivars in /lib/modules/6.2.xx of either of my kernels.
efivars is only in /sys/firmware/efi/efivars.

Wondering if the default location of efivars moved from each kernel ot /sys/firmware/efi?

---

