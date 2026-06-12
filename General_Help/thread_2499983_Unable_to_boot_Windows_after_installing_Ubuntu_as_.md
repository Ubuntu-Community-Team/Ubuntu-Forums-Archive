---
title: "Unable to boot Windows after installing Ubuntu as dual boot"
date: 2024-08-17
forum: General Help
---

### Post by bartek11 on 2024-08-17
I am unable to boot Windows after installing Ubuntu as dual boot. I started with:
[https://answers.microsoft.com/en-us/windows/forum/all/unable-to-boot-windows-after-installing-ubuntu-as/ef80e42c-27c4-4880-8cf2-84e543a487f8](https://answers.microsoft.com/en-us/windows/forum/all/unable-to-boot-windows-after-installing-ubuntu-as/ef80e42c-27c4-4880-8cf2-84e543a487f8)

and I follow 1st method and used boot repair tool.

I did not recover ubuntu after reboot and I would like to ask about help, boot repair tool returned link: [https://paste.ubuntu.com/p/8Jcn6HhSgF](https://paste.ubuntu.com/p/8Jcn6HhSgF)

I have installed windows 11 and I tried. to add ubuntu 24.04 on Samsung Galaxy Book4

---

### Post by oldfred on 2024-08-17
No need to post a link to the Boot-Repair instructions.

Post the link to the Summary report Boot-Repair offers to create which will show your system configuration.

What brand/model system?

If newer system and UEFI installs, you should always be able to boot either system from UEFI one time boot menu. Same boot key you used to boot USB flash drive. 

Grub only boots working Windows. That means fast startup which is hibernation must be off. And chkdks cannot be required. In those cases you boot Windows directly from UEFI boot menu & make fixes.

---

### Post by yancek on 2024-08-17
You need to install Grub in EFI mode as suggested at the end of the boot repair output.  Either that or boot the Ubuntu install media in UEFI mode (selected from the BIOS) and reinstall in UEFI mode.

Line 5 shows you have windows boot code in the MBR.
Lines 7-15 show an EFI partition and the contents which include ONLY windows files.
Line 118 shows the SSD on which windows/ubuntu are installed is a GPT drive which means windows must be installed in UEFI mode.  If you have windows in UEFI mode and install any LInux such as Ubuntu on the same drive (which you did), you must boot and install Ubuntu in UEFI mode.
Line 145 shows you have no fstab file which is necessary.
You might try to mount /dev/nvme0n1p7 from the Ubuntu install USB to check to see if there is an /etc/fstab file.  If not, reinstalling Ubuntu would be simpler.

---

