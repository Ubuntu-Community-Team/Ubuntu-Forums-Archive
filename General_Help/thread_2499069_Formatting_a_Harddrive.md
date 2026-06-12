---
title: "Formatting a Harddrive"
date: 2024-07-10
forum: General Help
---

### Post by angel mike on 2024-07-10
I bought a USB with Windows 10 pre-installed. Intend to use Windows on a temporary basis to update my Garman Satnav. I am getting an error on loading the usb ' Windows cannot be installed to this hard drive disk space - not formatted as NTFS'
What does this mean and how do I correct this.

---

### Post by currentshaft on 2024-07-10
More details, please.

What Windows USB did you buy? Where did you buy it? Did it ever work? Where in the boot process are you seeing this error? Most importantly, what troubleshooting steps have you already tried before asking for help?

---

### Post by oldfred on 2024-07-10
Windows does not run from any external devices like your USB.
You must have a USB installer which wants to install Windows onto your internal drive.

Windows requires MBR for BIOS or gpt for UEFI and empty/unallocated space or the correct set of partitions.
BIOS installs typically have a Boot partition and main NTFS partition.
UEFI installs require multiple partitions and formats, best to let installer create them.

You may want a virtual install if just using occasionally. Virtual-box or KVM

[https://ubuntuforums.org/showthread.php?t=2468297](https://ubuntuforums.org/showthread.php?t=2468297)

---

### Post by angel mike on 2024-07-11
Thanks for the responses-I think I will persevere with my own USB using Ventoy - it seems to be more straight forward option.

---

### Post by grahammechanical on 2024-07-11
I am going back into my memory of when I installed a Windows 8 trial version. I think that you first need to format that drive as NTFS. Then the USB will recognise the drive and allow an installation to be done. The operating system on the USB may have an option to format the drive.

Regards

---

