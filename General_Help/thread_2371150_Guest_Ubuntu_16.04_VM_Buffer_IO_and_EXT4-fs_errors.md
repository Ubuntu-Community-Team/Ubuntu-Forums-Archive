---
title: "Guest Ubuntu 16.04 VM: Buffer I/O and EXT4-fs errors"
date: 2017-09-11
forum: General Help
---

### Post by silversix311 on 2017-09-11
Hey guys,
First time posting here, I have been having issues with a virtual machine running Ubuntu on my W2012R2 server. It's been running for about a yearish without any issues other than my typical application troubleshooting for my Plex setup.

To give some background, I run Plex on a Dynamically Expanding VHDX. It originally was provisined with 92gigs as the max size, and I ended up hitting the max. I expanded the disk size to 301 GB, and booted parted magic to expand the partition within the VM. After doing so I have been getting Buffer I/O errors, and EXT4-fs warnings. I doubled checked the RAID0 SSD VM Store I have built and it has no errors and is functioning properly. None of my other VM's are affected, so it seems to be an issue with the VHDX/Partition within the VM. If anyone has any pointers on where to go to troubleshoot this issues, it would be greatly appreciated! Logs at bottom. Let me know if there are any other logs that are necessary to investigating this issue. Thanks!

**Configuration**
Host OS:
Windows Server 2012 R2
Hyper-V Running Ubuntu

Guest OS:
**Headless**
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

**Kernel Logs**
[https://pastebin.com/raw/fCzHzx3f](https://pastebin.com/raw/fCzHzx3f)

---

