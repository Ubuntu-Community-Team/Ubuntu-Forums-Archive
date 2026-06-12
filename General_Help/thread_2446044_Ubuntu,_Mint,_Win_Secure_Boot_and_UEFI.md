---
title: "Ubuntu, Mint, Win Secure Boot and UEFI"
date: 2020-06-23
forum: General Help
---

### Post by Kris_M on 2020-06-23
Writing this helped my understanding a bit. But I still have questions:

Just a few days ago, I changed my SSD to GPT and my windows partition to UEFI(manually)(don't ask)(you don't want to know!). Ubuntu 20.04 and Mint 19.3 were then installed.  Things have been booting and running fine with Secure Boot set ON in my BIOS. So apparently everything is signed. Apparently everything is UEFI. Any USB sticks I boot from seemingly have to be appropriate or they simply aren't seen as bootable.  Cool. I think...


It is not the DISK that is UEFI, but individual partitions of operating systems that are UEFI. - If I go to EASEUS Partition Mgr (sorry, I happened to be on win8.1 at the moment trying to suss something else) and explore the efi partition, I find essentially 3 sets of .efi stuff and some grub stuff - apparently one for each or my 3 operating systems. Created by the operating system installer? as a result of my having Secure Boot turned on???

IE if I shut Secure Boot off and then change operating systems, and then turn Secure Boot back on, the new opsys won't be bootable.  BUT, Can I have Secure Boot OFF most of the time and simply turn it on if I'm going to change operating systems?

If I shut off Secure Boot, I think I can boot any stick, either uefi or mbr. True?

**However**: will there be a problem if I use Rescatux or BootRepair or the like... - are they going to meddle with stuff in the efi partition??? You see my confusion.

I read somewhere that I have to have Secure Boot ON if I'm going to install something like linux or win, IF I want it to be bootable if Secure Boot is on. (?)

Or should I just leave Secure Boot on all the time. But outside of protection against rootkits I don't understand why.

I suppose Clonezilla won't care if Secure Boot is on or not, but if I tell Rescatux to redo the grub stuff, is that going to hose the stuff in the efi partition???

Thanks!

---

### Post by oldfred on 2020-06-24
Secure boot is internal to UEFI and requires all parts of boot process to be signed.
So boot loaders in ESP - efi system partition are signed.
Many have issues with Proprietary video or Wi-Fi drivers as Ubuntu cannot certify then and sign them. If a user believes then to be secure, he can provide his own key to sign them.

While there have been a very few UEFI/BIOS rootkit/virus', the main one years ago was issued by Sony to prevent users from playing music. It was a BIOS rootkit.

We may need Secure Boot in future if more virus' start to attack UEFI. But I do not currently use Secure Boot.

Now older. If you are a vendor who has major issues with virus, what better Marketing phrase than say system has Secure Boot, even though not related to almost every virus.
Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

From my link below:
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Secure Boot - [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

---

### Post by Kris_M on 2020-06-24
Thanks! So you don't use Secure Boot, so I likely can get away with not using it. Great.

But there is another choice: Boot UEFI or legacy. When I choose Secure Boot, it forces this to Boot UEFI only. But when I turn Secure Boot off, I can change that - what do you suggest?

When I, for example, install another linux, will it be set up with UEFI info in the efi partition if I have Secure Boot OFF and boot UEFI and legacy?

In other words, If I am going to run with Secure Boot OFF, why did I bother to set up things as UEFI?

Thanks!

---

### Post by oldfred on 2020-06-24
My motherboard from 2014 has UEFI or CSM, but if I choose the option that says UEFI or Legacy/CSM/BIOS (not sure which it says now), it only booted in BIOS mode. 

I had to change to UEFI only but with UEFI Secure boot off, which was called Windows mode or Other. And fine print said to use "Other" if Windows 7. Windows 7 does not support Secure Boot, so really Secure Boot setting. Every brand seems to call things somewhat slightly different. 

UEFI and BIOS are not really compatible. Once you start booting in one mode or other from UEFI, you cannot switch. Or grub only boots other installs in same boot mode.
And Windows only boots in BIOS from MBR and UEFI from gpt partitioned drives, so you absolutely cannot mix BIOS Windows with UEFI Ubuntu. Windows requires boot flag on its boot partition with boot files in BIOS mode and UEFI requires boot flag on the ESP. Only one boot flag allowed per drive, so Ubuntu should not even allow UEFI installs to Windows BIOS boot drives, but it does.

---

### Post by Kris_M on 2020-06-24
Thanks! 
My laptop dates back to 2012, and in BIOS for security allows Secure Boot or Disabled, and in Boot method allows UEFI only or UEFI and legacy (and maybe something else)
Okay, So I think you are suggesting keep it in UEFI only mode, which is no problem since I initially changed win8.1 to UEFI manually a couple days ago (it was on bios/mbr when I first installed it) and then installed the 2 linuxes, and all my USB sticks are (now) UEFI. I was able to run Boot Disk Repair this morning to uninstall one of the linuxes and all seems good and efi partition looks good. I would have no idea if something is UEFI other that in my BIOS I tell it to boot UEFI only.

Boot Disk Repair seems VERY UEFI savvy.

If I install Ubuntu with a UEFI stick, will it install it as UEFI?

---

### Post by oldfred on 2020-06-24
The setting in UEFI on which boot mode, is only for installed systems.
From UEFI boot menu, you can boot flash drive in either UEFI or BIOS mode.
And the mode you boot install media, UEFI or BIOS is then how it installs.
The Ubuntu ISO is configured for either UEFI or BIOS boot, but some installers that convert ISO to bootable system on flash drive may make it only one mode or the other.

Make sure you have latest UEFI for your system. Early UEFI often had bugs. For first few years it was hard to tell if UEFI issue, grub issue, or Ubuntu kernel or driver issue. And often all had some issues with some systems. Some users had so many issues they just stayed with BIOS boot. If you want to stay with BIOS, and do not have Windows better to use the newer gpt partitioning. But with BIOS and gpt you need a tiny 1 or 2MB unformatted partition with bios_grub flag. 

Before I had UEFI and for a few years after I added both an ESP - efi system partition and a bios_grub partition to every drive, so drive could be used for either, but grub reinstall required to convert from one to the other.

---

### Post by Kris_M on 2020-06-24
How would I know/check if I have the latest UEFI on my system? I changed win8.1 with gdisk64.exe which I had just downloaded.

if in windows go to [https://sourceforge.net/projects/gptfdisk/files/latest/download](https://sourceforge.net/projects/gptfdisk/files/latest/download)
gdisk-windows-1.0.5.zip

---

### Post by oldfred on 2020-06-24
You have to boot into BIOS or run some documentation file that shows BIOS version. Then go to your vendors support site and its update files. It may say Windows BIOS and is really an UEFI update. Does not matter if UEFI or BIOS.

Most UEFI systems have multiple ways to update, from Windows, from UEFI reading the update file from a FAT32 formatted partition, or from a DOS bootable update file. Linux now has updates for some newer systems also with fwupd.

I see my "BIOS" version in dmidecode, hardinfo, and lshw. Some of these you may have to add to a Linux install.

sudo lshw | grep -m 1 -A 25 "*-firmware"

---

### Post by Kris_M on 2020-06-25
I was going to say that that would just show me my BIOS version, but I checked and I had indeed missed one - mine was June '19 and latest was Sept '19 so I just put that on.

```
WHAT THIS PACKAGE DOES

  This package updates the UEFI BIOS (including system program and Embedded
  Controller program) stored in the ThinkPad computer to fix problems, add new
  functions, or expand functions as noted below.

  This program is language independent and can be used with any language system.


--------------------------------------------------------------------------------
CHANGES IN THIS RELEASE
  Version 2.77

[Important updates]
- Update includes a security fix.
- Update includes a security fix.
- Security fix addresses LEN-27764 ThinkPad Embedded Controller Update 
  Vulnerability(CVE-2019-6171). Refer to Lenovo's Security Advisory page for 
  additional information. 
   (https://support.lenovo.com/us/en/solutions/len-27764)
```

---

