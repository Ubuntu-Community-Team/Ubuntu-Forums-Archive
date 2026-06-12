---
title: "Toshiba 2'5  NVME SSD is not detected in Ubuntu 14.04.5 LTS"
date: 2022-02-15
forum: General Help
---

### Post by gkjhamca on 2022-02-15
Ubuntu 14.04.5 LTS does not detect  TOSHIBA disks but detect other NVME SSD from other vendor .


I believe that NVME SSD disk have native support in Ubuntu 14.04.5 ( Linux 4.4.0-133-generic ) so we don't need any driver to be installed .

nothing appear on dmesg  & kernel log related to the disk.

---

### Post by Perfect Storm on 2022-02-15
Is Ubuntu 14.04 at all supported anymore? My guess if you installed the latest LTS it will see your SSD. (Kernel 5.13 or 5.15)

EDIT: supported until Apr 2024

---

### Post by gkjhamca on 2022-02-15
We have some legacy stuff which needs to run on Ubuntu 14.04 . For NVME SSD do we have a specific driver from vendor or it is supported with native OS support .

---

### Post by Perfect Storm on 2022-02-15
> **gkjhamca said:**
> We have some legacy stuff which needs to run on Ubuntu 14.04 . For NVME SSD do we have a specific driver from vendor or it is supported with native OS support .

If the SSD is new as newly bought, I highly doubt it's supported by a 4.xx kernel.

---

### Post by mIk3_08 on 2022-02-15
> **gkjhamca said:**
> Ubuntu 14.04.5 LTS does not detect TOSHIBA disks but detect other NVME SSD from other vendor .
I believe that NVME SSD disk have native support in Ubuntu 14.04.5 ( Linux 4.4.0-133-generic ) so we don't need any driver to be installed .
nothing appear on dmesg & kernel log related to the disk.
Thus your ssd detected by your bios/uefi? Because if not, there will be something wrong with your ssd. Because this happen sometimes that it can be detected via i/o external device but can't be detected on the bios/uefi. This is strange but its possible.

---

### Post by DuckHook on 2022-02-15
> **Perfect Storm said:**
> Is Ubuntu 14.04 at all supported anymore? My guess if you installed the latest LTS it will see your SSD. (Kernel 5.13 or 5.15)

EDIT: supported until Apr 2024
Only if OP signed up for ESM. Otherwise, support stopped in 2019.
> **Perfect Storm said:**
> If the SSD is new as newly bought, I highly doubt it's supported by a 4.xx kernel.
+1
> **gkjhamca said:**
> We have some legacy stuff which needs to run on Ubuntu 14.04 . For NVME SSD do we have a specific driver from vendor or it is supported with native OS support .
NVME has native kernel support but only in more current kernels. NVME wasn't much of a thing five years ago.

I'm not well versed in the fine points of ESM support and do not know how thoroughly they update old kernels to handle new HW, but my recommendation would be to consider running a current OS, then running your legacy stuff in a 14.04 VM or container. That's what I do with old WINE versions that rely on old OSes. I have a LXD container going back to 12.04 just to run a bunch of retro games.

---

### Post by Perfect Storm on 2022-02-15
> I'm not well versed in the fine points of ESM support and do not know how thoroughly they update old kernels to handle new HW, but my recommendation would be to consider running a current OS, then running your legacy stuff in a 14.04 VM or container. That's what I do with old WINE versions that rely on old OSes. I have a LXD container going back to 12.04 just to run a bunch of retro games.

+1

---

### Post by coffeecat on 2022-02-17
Support, not chat.

*Thread moved to **General Help**.*

---

