---
title: "Your kernels are unsigned. This system will fail to boot in a secure boot environment"
date: 2018-12-08
forum: General Help
---

### Post by jiapei100 on 2018-12-08
```
E: Your kernels are unsigned. This system will fail to boot in a secure boot environment.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
```

---

### Post by oldfred on 2018-12-09
What version of Ubuntu?
       cat /etc/*release 

What Brand/model system?

I am using 18.04 and have grub-efi-amd64-signed installed, but no signed kernels. But do not plan on turning on UEFI Secure boot in the near future. Perhaps in future is major issues develop, I then may turn it on.

---

