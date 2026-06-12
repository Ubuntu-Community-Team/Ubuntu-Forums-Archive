---
title: "Raid Not Detected"
date: 2016-12-06
forum: General Help
---

### Post by morpheusx2 on 2016-12-06
I am currently trying to setup Ubuntu 16 on the following hardware

MSI Z170A Gaming M5
MSI GTX 1080 
DDR4 64 GB RAM 2100MHZ
2x M.2 SSD Samsung 950 PRO

I have installed and ran ubuntu on a regular hardrive and its ran fine, Setting up the graphics drivers was a nightmare but I eventually got it working , Tested L4D2 @ 144FPS , Ran great.

I am trying to get Ubuntu during install to detect the RAID 0 M.2 Raid that is setup in the bios. How can I get it to detect the raid ?

---

### Post by courtney2 on 2016-12-07
I found it easier to do MDADM RAID during the installation for my SSDs. I however, did RAID 1. Did you set RAID in your BIOS instead of AHCI or NVMe? I would honestly recommend going this route, this is the not-so-fancy looking installer though, not sure how to get this installer on plain ubuntu

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

EDIT: I might be wrong, but I think I remember hearing Linux actually doesn't support that RAID boot option that is in most BIOS...take that with a grain of salt. I have read about those fancy Microsoft assured/whatever laptops that make it impossible to install Linux because their BIOS is set to the RAID boot option, and it's some funky proprietary type of RAID

---

### Post by morpheusx2 on 2016-12-07
The raid in the BIOS uses some sort of NVMe Mapping for the m.2 drives. Its the only raid support for those 2 drives. If one drive is installed its used like a hybrid, If 2 then it becomes a raid automatically.

---

### Post by courtney2 on 2016-12-07
I personally don't know about setting up RAID from BIOS, I have only worked with a hardware RAID controller once, and have done software RAID a couple times for non-storage devices, but my own recommendation is to set your BIOS to NVMe since you have good PCIe drives then use MDADM for software RAID 0.

---

