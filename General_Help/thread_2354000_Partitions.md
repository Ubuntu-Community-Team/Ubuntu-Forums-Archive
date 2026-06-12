---
title: "Partitions"
date: 2017-02-27
forum: General Help
---

### Post by aris-ko on 2017-02-27
Hi,

I would like to dual boot my pc with ubuntu, but i don't know which partition i should delete. These are my partitions.
1. Healthy (OEM Partition)       970MB
2. Healthy (Recovery Partition)  840MB
3  Healthy (EFI System Partiton) 260MB
4. C                             900 GB
5. Healthy (Recovery Partition)  25GB

Any help will be appreciated. 
Thanks in advance.

---

### Post by RobGoss on 2017-02-27
Hello and welcome, I don't see any reason why you would want to delete anything. You should be able to just shrink your primary Windos partition and use the unallocated space to install Ubuntu 

The partitions you see belong to Windows deleting anything will cause problems with Windows booting

Please post the specs for your machine in order for people to help you

---

### Post by oldfred on 2017-02-27
Post this just to confirm details of configuration:
sudo parted -l

Normally if you have an ESP - efi system partition you have gpt and no limit on partitions.
But a few vendors started using FAT32 with old BIOS/MBR installs and somehow it is shown as an efi partition.

---

