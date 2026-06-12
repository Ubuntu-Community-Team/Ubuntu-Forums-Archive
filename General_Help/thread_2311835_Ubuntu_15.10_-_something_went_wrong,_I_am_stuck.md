---
title: "Ubuntu 15.10 - something went wrong, I am stuck"
date: 2016-01-30
forum: General Help
---

### Post by anastas.petkovcee on 2016-01-30
Hi all,

I've been using Ubuntu dekstop for a month or so without issues.

Today however something went wrong:
- the USB ports do not work
- the OS cannot detect any network devices
- I seem to have lost my superuser privilages

I really do not know what to do. I cannot even backup my files to an external HDD or over the network and re-install.

When I run the installation CD and go to "Try Ubuntu" the ports and network work, but I cannot access my files.

Can anyone help?

Thanks

---

### Post by anastas.petkovcee on 2016-01-30
I think I've just figured it out.

I must have installed a new kernel which doesn't work with my configuration. When I went to the boot list and selected the previous version - 4.2.0.22, everything worked. 4.2.0.23 is giving me those issues.

---

