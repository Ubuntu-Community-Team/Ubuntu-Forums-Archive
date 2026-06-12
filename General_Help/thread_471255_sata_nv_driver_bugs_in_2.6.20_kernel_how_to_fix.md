---
title: "sata_nv driver bugs in 2.6.20 kernel: how to fix?"
date: 2007-06-11
forum: General Help
---

### Post by cshubu on 2007-06-11
The Linux 2.6.20 kernel and later has bugs in the adma support, especially in the sata_nv driver.

When I was running Slackware, I added this line to lilo.conf to turn off adma support:

        append = "sata_nv.adma=0"

This disabled adma support, but NCQ and normal DMA worked fine, and I had no trouble this way.

I installed Kubuntu 7.04 and had the same issue, so I configured grub to pass the same kernel command option to disable adma, like so:

kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=12b5bb87-45ba-4706-9822-57424b3c0204 ro sata_nv.adma=0 quiet splash

However, when the machine boots, I get this message:

[   22.412850] Unknown boot option `sata_nv.adma=0': ignoring

Am I adding the kernel command option incorrectly or what?

I really need this to work because this bug has been around since 2.6.19, and so far doesn't appear to have been fixed.

Thanks for any help or pointers.

---

### Post by airblade on 2007-06-15
[http://bugs.launchpad.net/ubuntu/+bugs](http://bugs.launchpad.net/ubuntu/+bugs)
Try searching for your problem here. If you don't find any solution, add the bug.

---

