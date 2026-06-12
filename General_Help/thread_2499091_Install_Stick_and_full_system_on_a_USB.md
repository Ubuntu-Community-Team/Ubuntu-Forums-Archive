---
title: "Install Stick and full system on a USB"
date: 2024-07-11
forum: General Help
---

### Post by asearle on 2024-07-11
Dear All,

I have Ubuntu on ...

a.) an install-stick for installing or trying out a system from a USB-stick
b.) A live-stick with a full-running Ubuntu (i.e. to run from the stick)

In the past it was no problem to boot from either but recently I have been having problems booting from the fully-installed live-stick.  On older computers both versions work but on newer computers the install-stick (a) is recognised and bootable but the live-stick (with the installed system, b) is not visible.

Any ideas about this?  Could it be UEFI-issue?  Can/should I change the UEFI-settings? And/or should I set up the live-stick (with the installed system) differently?

Many thanks for any tips that you can give me.

Yours,
Alan in Cologne

---

### Post by currentshaft on 2024-07-11
What version of Ubuntu?

What type of device?

It's probably related to UEFI/secure boot settings. Sadly, legacy BIOS is quickly disappearing in newer hardware.

---

### Post by asearle on 2024-07-11
Thanks for the quick reply.

This is Lubuntu 24.04 on a standard usb-stick.

Indeed, yes, my worry is that it is a UEFI/Secure-boot issue.

So can you give a general answer on whether it is possible to tweak the UEFI settings so that the live-stick (with Lubuntu pre-installed) is visible/bootable?  Or is this only possible with older BIOS models?

If I know that it can't be done, that would save me a lot of fishing around.

If you think it can be done, I can send details of the BIOS.

Many thanks,
Alan

---

### Post by TheFu on 2024-07-11
You'll need to research the specific BIOS for your motherboard. Each motherboard will have a different BIOS and different versions of the BIOS for a specific motherboard can have different features enabled or disabled.  Legacy booting and/or UEFI would be typical options.  I suppose low-end motherboards or very specialized ones, might only support UEFI booting.  I've never seen limited BIOSes, except in really cheap laptops and typically they didn't include VTx or AMD-v support.  Of course, nobody has seen everything, so there are exceptions.

My Ryzen Asus B450 and B550 motherboards support legacy and UEFI booting.  The BIOS is motherboard specific, so nobody can answer the question.

---

### Post by currentshaft on 2024-07-11
If you have access to another Ubuntu host, use Startup Disk Creator to make the bootable USB and install Ubuntu using it. That helped me get it working on newer, UEFI-only systems.

---

### Post by oldfred on 2024-07-11
You can install both versions of grub to an install. Grub-efi-amd64 for UEFI boot and grub-pc for BIOS boot.
Not sure if you also can have the Secure boot or signed version also. And updates may get then out of sync and cause issues.
Best just to have one USB as UEFI and another as old BIOS, if you still need old BIOS boot?
I have an external SSD with Kubuntu and just restalled grub-efi-amd's signed version, but have not yet tested on on my laptop that is Secure Boot.
My desktop is UEFI, but not Secure Boot.

Best if all UEFI drives are gpt.
And you can use gpt with BIOS boot, except for Windows which requires MBR(msdos) for BIOS boot.

I have multiple flash drives with full installs and use grub's loopmount to boot ISO on external drives.
But since starting to use a SSD M.2 card in a USB adapter, I will not buy any more flash drives. SSD is almost as fast as it was when internal drive.

Post this in code tags to preserve formatting:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,parttype

---

