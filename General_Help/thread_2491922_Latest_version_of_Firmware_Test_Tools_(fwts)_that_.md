---
title: "Latest version of Firmware Test Tools (fwts) that will boot on 32-bit OS only UEFI?"
date: 2023-10-25
forum: General Help
---

### Post by mbhaber on 2023-10-25
Latest as of posting is 23.09.00 is a 64-bit OS live image, so I need a 32-bit OS live image. Thanks.

---

### Post by deadflowr on 2023-10-25
Sorry, Ubuntu does not create 32-bit images anymore.

---

### Post by grahammechanical on 2023-10-25
This is what the OP is talking about

[https://uefi.org/sites/default/files/resources/fwts_uefi_0920_2013.pdf](https://uefi.org/sites/default/files/resources/fwts_uefi_0920_2013.pdf)

Does the OP want a 32 bit version of this utility? I do not know? Is he using a machine with a 32bit UEFI? Years ago there were notepad machines that had 64 bit CPUs but 32 bit UEFI. It was very difficult to install Ubuntu on them.

I do not understand what the OP wants.

Regards

---

### Post by MAFoElffen on 2023-10-25
> **grahammechanical said:**
> This is what the OP is talking about

[https://uefi.org/sites/default/files/resources/fwts_uefi_0920_2013.pdf](https://uefi.org/sites/default/files/resources/fwts_uefi_0920_2013.pdf)

Does the OP want a 32 bit version of this utility? I do not know? Is he using a machine with a 32bit UEFI? [COLOR=#ff0000]Years ago there were notepad machines that had 64 bit CPUs but 32 bit UEFI.[/COLOR] It was very difficult to install Ubuntu on them.

_I do not understand what the OP wants._

Regards
I have an example of one of those machine here: an old MAC Probook, that I have Ubuntu 22.04 on, to help me test and verify my 'system-info' script on that hardware. 

32bit EFI and 64bit CPU. It "is" a pain to install to fresh. I actually have that setup as a multi-boot.

My question is that if he is asking if he can compile and run it from a 32bit OS? ...or run it on 64bit and test 32bit EFI? That is two very different scenarios.

The source code is here: [https://github.com/ColinIanKing/fwts](https://github.com/ColinIanKing/fwts)

The Ubuntu wiki reference for it is here: [https://wiki.ubuntu.com/FirmwareTestSuite/Reference?action=show&redirect=Kernel%2FReference%2Ffwts](https://wiki.ubuntu.com/FirmwareTestSuite/Reference?action=show&redirect=Kernel%2FReference%2Ffwts)

---

