---
title: "How can I sign drivers in order to bypass uefi?"
date: 2018-02-26
forum: General Help
---

### Post by koene2 on 2018-02-26
Hi all,

I've downloaded the latest displaylink drivers (displaylink-driver-4.1.9.run) and would like to sign this before I install. ON the diisplaylink website it says 'Alternatively, users must sign the evdi kernel module themselves.'
The only description I found is [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules) but I don't know what the 'module' is in here. Is that the *.run filename? How can I sign this driver?

Kind regards

---

### Post by sudodus on 2018-02-26
Can you turn off secure boot in a UEFI-BIOS menu? Then you need no signature on the drivers.

---

### Post by koene2 on 2018-02-26
> **sudodus said:**
> Can you turn off secure boot in a UEFI-BIOS menu? Then you need no signature on the drivers.
Yes I can but than no boottable device is found and i can not set it in the bios menu (only possible when secure boot is on )

---

### Post by sudodus on 2018-02-26
That is strange, I would have expected the opposite.

Are you sure that you turned off secure boot, but stay with UEFI mode? I could expect that behavour, if you turn off UEFI and try to boot in BIOS mode (alias CSM alias legacy mode).

Let us hope someone who knows more about this will chip in and help.

---

### Post by koene2 on 2018-02-26
> **sudodus said:**
> That is strange, I would have expected the opposite.

Are you sure that you turned off secure boot, but stay with UEFI mode? I could expect that behavour, if you turn off UEFI and try to boot in BIOS mode (alias CSM alias legacy mode).

Let us hope someone who knows more about this will chip in and help.

I tried this again (after I installed without turning off secure boot), and now I can use 3 screens via displaylink (so it seems the drivers are working now).
TY!

---

### Post by sudodus on 2018-02-26
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

