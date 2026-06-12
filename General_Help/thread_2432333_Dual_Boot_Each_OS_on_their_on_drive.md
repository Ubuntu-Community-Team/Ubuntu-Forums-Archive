---
title: "Dual Boot: Each OS on their on drive"
date: 2019-11-30
forum: General Help
---

### Post by SnuKies on 2019-11-30
I have searched over the internet, but what I could find referred to partitioning the HDD and installing a part of linux there

I've recently bought an Asus TUF fx505dt which comes with both HDD and SDD. I have installed the Windows on HDD (by partitioning it in 2 drives - C: and D:) and decided to install Ubuntu 18.04 on the SDD, without partitioning it at all (so the whole sdd is the / )

The problem is that I don't get to the GRUB menu at all. If I want to boot Ubuntu I have to go to BIOS and change the boot priority.

Is there any way I can solve this? I can reinstall the Ubuntu, no problem, or what can I do to have the GRUB menu at startup again?

---

### Post by oldfred on 2019-11-30
Are you installing both in same boot mode? Both UEFI (since new systems are UEFI) or both BIOS which is now 35 years old.
Windows only boots from MBR with BIOS and only in UEFI from gpt. So knowing partitioning of Windows drive will tell if UEFI or BIOS.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues, do not run until someone reviews report.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yancek on 2019-11-30
I noticed that you did not mention which version of windows you are using.  This is important information since microsoft has been licensing the windows OS since 1985.  If someone posts here without that information, we are left to guess and are not always correct but the boot repair script will proivide all that information.

---

### Post by SnuKies on 2019-12-01
[http://paste.ubuntu.com/p/GnCJhNsYpr/]("http://paste.ubuntu.com/p/GnCJhNsYpr/?fbclid=IwAR1AX4Cn3TeP-FpeZrB7qWL4xDH_D_6VpYSFB9kaNLumFmOB-RCBcM19Ds4")

Yes, I forgot to mention it's Windows 10

---

### Post by oldfred on 2019-12-01
It looks like you ran Boot-Repair in BIOS boot mode. You should always be using UEFI.
Your Windows install in sda is UEFI and sda is gpt partitioned.

It looks like your NVMe drive is MBR(msdos) partitioned, so most likely a BIOS install.
You really want UEFI install, but must have gpt partitioning & an ESP - efi system partition on the NVMe drive. In UEFI mode, Ubiquity only wants to install grub to the first drive's ESP.

You only need an ESP (FAT32 with boot flag/ESP flag) about 500MB and / (root), but many of use like smaller / and larger /home or data partition. I have multiple / on SSD and large data partitions on HDD (no Windows).

See link below in my signature for UEFI install info. 9 easy steps.

---

