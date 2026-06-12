---
title: "No Boot Disk has been Detected or the Boot Disk has failed."
date: 2013-09-28
forum: General Help
---

### Post by pipiepie1 on 2013-09-28
I have an Acer Aspire X computer with Windows 8 preinstalled. The OS started acting up so I decided to delete Windows and install Ubuntu. First I installed 12.04 LTE and got the error:

No Boot Disk has been Detected or the Boot Disk has failed.

I deleted 12.04 and installed 13.04 but the message still persists.

The BIOS looks fine and I can access all of the computer files through the LiveCD. What do I do?

-Andrew

---

### Post by sudodus on 2013-09-28
Welcome to the Ubuntu Forums :-)

When you can run the computer and access the computer files through the live CD you will also succeed with the installation.

I think you have problems because of the settings in the BIOS for Windows 8.

- UEFI (can be managed by Ubuntu, but is not necessary without Windows 8. Can it be swiched off (to legacy BIOS or CSM)?

- Secure boot. Try to switch it off if possible (in a BIOS menu).

- Fast boot. Try to switch it off if possible (in a BIOS menu).

See this link to get started with more details [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

