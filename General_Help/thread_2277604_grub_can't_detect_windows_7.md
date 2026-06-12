---
title: "grub can't detect windows 7"
date: 2015-05-10
forum: General Help
---

### Post by xtl on 2015-05-10
Hello. I've got a problem with dual-booting Windows 7 and Kubuntu 15.04. Month or so ago everything was fine until I've had to reinstall Windows - now update-grub only detects Linux. I tried using grub-repair's recommended repair, but it didn't fix the issue. Thanks in advance for any help.

---

### Post by yancek on 2015-05-10
After re-installing windows, did you  re-install the Kubuntu Grub bootloader?  If not, what are you using to boot Kubuntu?  The boot repair script generally outputs a boot info summary report as a text file.  Do you have that?  You will need to post it or some more detailed information.

---

### Post by xtl on 2015-05-10
yes, i've reinstalled grub through apt-get
this is text file when I used boot repair from live cd: [http://paste.ubuntu.com/11046289/](http://paste.ubuntu.com/11046289/) I ran it once more on hard drive and its output is slightly different: [http://paste.ubuntu.com/11063857/](http://paste.ubuntu.com/11063857/) I posted both because I wasn't sure

also Win7 is on /dev/sdc, for some reason it detects WinXP on sda (?)

---

### Post by oldfred on 2015-05-10
You have a couple of issues.
You must have a newer system with UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Windows 7 and later normally uses two partitions. One is the Boot partition and the main install.
It looks like you installed to sdc, but had CSM/BIOS set to boot from sda, so the Windows Boot partition files went into the sda1 partition. You should be able to copy/move or repair the install in sdc to have bootmgr & BCD so you can directly boot sdc in BIOS mode. But that requires Winows repair tools. Not sure if just copy of those files works or not without Windows repairs also.

You installed Ubuntu into sdb in UEFI boot mode on a gpt drive. You will not be able to dual boot from grub menu as UEFI and CSM are not compatible. You have to reboot to switch modes. And some systems will work from one time boot key, others require you to turn on/off UEFI or CSM settings in UEFI to boot system installed in that mode.

You can also convert Ubuntu install to CSM/BIOS boot by adding a tiny 1 or 2MB bios_grub partition on sdb and using Boot-Repair booted in BIOS mode to uninstall/reinstall grub. It uninstalls the grub-efi-amd64 and installs grub-pc for BIOS boot.

Do not run auto fix in Boot-Repair in BIOS as that reinstalls grub to every MBR, and you want to keep a Windows boot loader in sdc, so you can directly boot it if need be or if you do not convert Ubuntu to CSM boot.

---

