---
title: "Kernel compiling for newbie: error message during boot"
date: 2007-05-04
forum: General Help
---

### Post by kilou on 2007-05-04
Hi,

I'm using Feisty on my laptop and to save some battery power I want to undervolt my laptop and I also need to remove the mutli-processor support in the kernel because it's preventing CPU scaling to work correctly on my computer (I have a single proc, centrino). To do so I've downloaded the 2.6.20.11 kernel from [www.kernel.org](www.kernel.org) and patched it with Linux PHC to allow undervolting. I had saved all the settings in my "old" Feisty kernel and did apply them to the new kernel. Everything works fine with the new compiled kernel and the computer boots correctly but I'm just annoyed by two lines that popup during the boot process, just before the boot screen is loaded. The message is as follow:

Starting...
uncompressing linux kernel
XXXX PCI: BIOS Bug: MCFG area at e00000000 is not E820 reserved
XXXX PCI: not using MMCONFIG

There are numbers in place of the XXXX but they change at every boot.

So these errors seem related to PCI and I guess this is probably due to the kernel configuration settings for "PCI Access mode". My setting is set on "Any" which is the default but I learned that "Any" means that Linux first tries to detect PCI devices with MMCONFIG, then tries direct access and at last tries with BIOS. If I understand well MMCONFIG is for PCIExpress and I don't have that so this is probably why I get "not using MMCONFIG" message. But what about the BIOS bug??? If I get a BIOS bug it means that both direct access and BIOS access do not work to detect PCI (because "Any" tries direct access before BIOS access)........so PCI shouldn't work at all???

Do you know what would cause the error "BIOS Bug: MCFG area at e00000000 is not E820 reserved" and what setting I should change in the kernel to correct that??

Thanks

---

### Post by dannyboy79 on 2007-05-04
according to here: [http://www.mail-archive.com/linux-scsi@vger.kernel.org/msg04930.html](http://www.mail-archive.com/linux-scsi@vger.kernel.org/msg04930.html)
it's really nothing to be concerned with I wouldn't think. i have this show up in my dmesg all the time and nothing is affected by it.

ACPI-0517: *** Error: Method parse/execution failed [\_PR_.CPU1._PDC] (Node dfffe1e0), AE_BAD_HEADER
[17179574.964000]     ACPI-0517: *** Error: Method parse/execution failed [\_PR_.CPU2._PDC] (Node dfffeee0),
AE_BAD_HEADER

sorry I couldn't be of more help

---

### Post by kilou on 2007-05-04
Well if that is nothing to worry about it's helpful :) Thanks. It's just curious why this happens with the Vanilla kernel and not with the Ubuntu one with exact same parameters (except some about processor but nothing related). I've had this error everytime I used a Vanilla kernel. I got exactly the same when using the 2.6.17 vanilla kernel under Edgy.

Nothing to worry about then but it would just look better without error message :lolflag:

---

