---
title: "[PROBLEM] Ubuntu won't recognize Intel RST NVMe M.2 RAID0"
date: 2018-06-03
forum: General Help
---

### Post by tomer38 on 2018-06-03
Hello,

I used my bios to create a RAID 0 array using two NVMe M.2 SSDs (Intel RST).

Upon launching Ubuntu 18.04 installation, no raid array is being detected.

When trying to launch mdadm --detail-platform, I receive a response from Intel RST, but no devices are shown to be attached.

While doing the same with **SATA **SSDs - **it works just fine**.

To make things clear - when disabling RAID in bios - Ubuntu recognizes both my NVMes, and when using the alternative installer - I'm able to create a RAID array but it seems to fail when trying to install GRUB.

I also know the RAID problem is a known issue in Windows installations, and it can be solved by pushing new Intel RST drivers to the windows installation.

Any ideas what can I do to make it work?

Thanks.

---

### Post by adam-hardy on 2018-06-05
well you've got my sympathy - I have exactly the same problem. I set up 2 M.2 SSDs with Intel RST RAID in the UEFI of my new Gigabyte motherboard, but the Ubuntu server installer doesn't see anything there. 

I was about to try mdadm instead. So you set up a software RAID with mdadm but grub won't boot the installation on it?

Just to keep the links together, I had posted this on askubuntu, but got 35 views and no comments or answers :(

[https://askubuntu.com/questions/1042778/ubuntu-18-04-server-and-raid-fakeraid-or-hardware-or-mdadm](https://askubuntu.com/questions/1042778/ubuntu-18-04-server-and-raid-fakeraid-or-hardware-or-mdadm)

did you read up the links from one of the other poster's footer:
> 
    Ubuntu now installs with Intel SRT on, but when grub sees the RAID  grub will not install. So you have to turn the SRT off or set UEFI/BIOS  to AHCI and remove the RAID meta data from the drives. Some install  Ubuntu to SSD, others install to hard drive and turn SRT back on and  have had it work.
 Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929) 

---

### Post by tomer38 on 2018-06-06
Well, too bad.

Actually I found a workaround to solve this issue - I just installed Ubuntu server on two SATA SSDs (without enabling RAID in the bios), and then dd'd them to NVMEs. Works like a charm!

---

### Post by adam-hardy on 2018-06-06
Oh right so you gave up on RAID completely?

---

### Post by tomer38 on 2018-06-07
I gave up enabling RAID in the BIOS.

I used Ubuntu server alternative installer to install it on RAID0 (using two SATA SSDs), then dd'd those two to NVMEs, and it works great (Ubuntu on RAID0 using two NVMEs M.2).

---

