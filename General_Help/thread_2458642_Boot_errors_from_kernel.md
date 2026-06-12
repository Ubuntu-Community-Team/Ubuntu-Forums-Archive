---
title: "Boot errors from kernel"
date: 2021-03-01
forum: General Help
---

### Post by byte27 on 2021-03-01
Hi, I'm new to this forum. I'm asking help some errors that I'm facing after boot. Everything works perfectly but I want to understand and solve the errors. I'm running Ubuntu 20.10 with kernel 5.8.

```
 ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.LPC0.EC0], AE_NOT_FOUND (20200528/dswload2-162)
 ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20200528/psobject-220)
 pci 0000:00:00.2: AMD-Vi: Unable to read/write to IOMMU perf counter.
[drm:dm_helpers_dp_write_dpcd [amdgpu]] *ERROR* Failed to find connector for link!
[drm:dm_helpers_dp_write_dpcd [amdgpu]] *ERROR* Failed to find connector for link!

```

---

### Post by CelticWarrior on 2021-03-01
[https://askubuntu.com/questions/1030310/acpi-error-ae-not-found-with-same-motherboard-replaced](https://askubuntu.com/questions/1030310/acpi-error-ae-not-found-with-same-motherboard-replaced)
[https://stackoverflow.com/questions/62827591/amd-vi-unable-to-read-write-to-iommu-coun-problem-loading-x-509-certificate](https://stackoverflow.com/questions/62827591/amd-vi-unable-to-read-write-to-iommu-coun-problem-loading-x-509-certificate)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1893624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1893624)

---

### Post by byte27 on 2021-03-01
In the last link he solved the problem going back from 5.8.5 to 5.8, but I'm already on 5.8

---

