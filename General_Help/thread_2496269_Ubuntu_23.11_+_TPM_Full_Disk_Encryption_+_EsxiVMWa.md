---
title: "Ubuntu 23.11 + TPM Full Disk Encryption + Esxi/VMWare"
date: 2024-03-21
forum: General Help
---

### Post by Glencore on 2024-03-21
Hello,

Has anyone gotten TPM + FDE working on a VM in ESXi?

I got through the installation but after reboot the system would not start, a screen comes up with /EndEntire and then the following errors:

[IMG]https://i.postimg.cc/wvHmFbBN/image.png[/IMG]

When booting from the LiveCD, I get responses from the TPM module.. such as sudo tpm2_pcrread, sudo tpm2_getcap

---

### Post by TheFu on 2024-03-21
You probably already know this, but ESXi is dead for non-paying users.  If you are paying for it, I'd suggest contacting VMWare support.  If you aren't paying, you need to move off that platform ASAP.

[https://arstechnica.com/information-technology/2024/02/broadcom-owned-vmware-kills-the-free-version-of-esxi-virtualization-software/](https://arstechnica.com/information-technology/2024/02/broadcom-owned-vmware-kills-the-free-version-of-esxi-virtualization-software/)
[https://kb.vmware.com/s/article/2107518](https://kb.vmware.com/s/article/2107518)

BTW, there is no Ubuntu 23.11 release.

---

