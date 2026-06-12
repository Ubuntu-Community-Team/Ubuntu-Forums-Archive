---
title: "triple+ booting setup with uefi"
date: 2015-01-13
forum: General Help
---

### Post by Jlm1984 on 2015-01-13
Ok so I'm fairly new to Linux although I've used it on and off, I just built a new pc and I plan on recording music and thought I'd give unbuntu studio a goI'd also like to have another distro of Linux and have Windows 8I don't believe I have secure boot as I was able to install ubuntu 14.10 with no issuesNow this is my sole operating system at the moment, how should I proceed from this point as most guides I've read assume that Windows is installed first.Thanks for any and all input

---

### Post by oldfred on 2015-01-14
Windows has specific partition requirements. But will reuse the existing efi partition and add a folder for its boot. You still need to turn its fast boot off. It should work with secure boot on or off.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If installing another Ubuntu family or related system, backup efi partition first. Probably should anyway. I installed a second Ubuntu on my sdb, and specified that grub should be in efi partition on sdb, but it overwrote my efi partition on sda. I could still dual boot thru grub menu but also wanted separate efi boot on different drives.
If not Ubuntu family it will create a new folder in efi partition with its own name.

What brand/model motherboard? What video card?

---

### Post by Jlm1984 on 2015-01-16
I figured it all out, I installed Windows 7 first, then I installed deepin distro, and finally ubuntu studio, I use grub 2 to boot them all successfully 

. I have a Msi motherboard with onboard Radeon I believe
But all seems to be working good now tha me for your advice

---

