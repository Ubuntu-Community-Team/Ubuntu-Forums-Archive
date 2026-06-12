---
title: "Grub can't find Windows 7"
date: 2014-10-01
forum: General Help
---

### Post by dunn-stephen on 2014-10-01
Hi everybody, I have a Windows 7 installation on /dev/sda (it's own drive with 1 NTFS partition). Ubuntu 14.04.1 is on /dev/sdb. Before I upgraded from 12.04 I had a grub menu option for Windows 7, but after the update it has disappeared. I have tried:

```

sudo os-prober
sudo update-grub

```

I can mount the drive with

```
sudo mount /dev/sda1 /media/windows
```

but that doesn't help grub or os-prober. I also installed and ran boot-repair ([by this method]("http://askubuntu.com/questions/449818/cant-find-boot-repair-package-for-the-newest-version-of-ubuntu")) but it didn't help either.

Does anyone have any idea how to get grub to locate my Windows installation? (The "Advanced options" boot menu just shows various version of previous linux headers.)

---

### Post by Bucky Ball on 2014-10-01
```
sudo update-grub
```

You left out the hyphen. ;)

Give that a try and see if it works.

---

### Post by dunn-stephen on 2014-10-01
No sorry that was a typo, I did it correctly. Any other ideas?

---

### Post by oldfred on 2014-10-01
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dunn-stephen on 2014-10-02
[Here]("http://paste.ubuntu.com/8479372/") is the link to my bootsummary. It says "GPT detected. Please set the grub_bios flag..." However, I tried setting that flag on the EFI partition with gparted and still received the same message.

---

### Post by Dennis N on 2014-10-02
Looks like on sdb Ubuntu is installed in UEFI mode, while on sda Windows is installed in BIOS mode. You can't boot BIOS systems from UEFI grub - they won't even show up on the menu.

Ubuntu needs to be installed in BIOS mode too.

---

### Post by oldfred on 2014-10-02
Do not reinstall unless you use Something Else. 

You can convert the UEFI install in sdb to BIOS boot with Boot-Repair, but do have to have a bios_grub partition.
That partition is not the efi partition which is for UEFI boot. The bios_grub is 1 or 2MB unformatted with the bios_grub flag set. Use gparted to create that partition anywhere on sdb and then rerun Boot-Repair and convert from UEFI to BIOS boot. Be sure to install grub2's boot loader to sdb, so you keep a Windows boot loader in sda.

Gparted uses the boot flag to identify the efi partition, so the boot flag should only be on the efi partition. You can dual boot with Windows in BIOS and Ubuntu in UEFI, but only can choose from UEFI or perhaps one time boot key, not from grub menu. 

UEFI & BIOS are not really compatible and once you start booting in one mode you cannot switch, or once grub is loaded in one mode or the other, you cannot boot any other system in a different boot mode.

---

### Post by dunn-stephen on 2014-10-02
> **Dennis N said:**
> Looks like on sdb Ubuntu is installed in UEFI mode, while on sda Windows is installed in BIOS mode. You can't boot BIOS systems from UEFI grub - they won't even show up on the menu.

Ubuntu needs to be installed in BIOS mode too.

I want to keep the newer UEFI mode though, and this was all working fine until I upgraded to 14.04.1. I had a Windows option in my grub menu and I don't understand why I need to be resizing partitions and setting flags all of a sudden. Does anybody know the reason behind this?

---

### Post by dunn-stephen on 2014-10-02
> **oldfred said:**
> Do not reinstall unless you use Something Else. 

You can convert the UEFI install in sdb to BIOS boot with Boot-Repair, but do have to have a bios_grub partition.
That partition is not the efi partition which is for UEFI boot. The bios_grub is 1 or 2MB unformatted with the bios_grub flag set. Use gparted to create that partition anywhere on sdb and then rerun Boot-Repair and convert from UEFI to BIOS boot. Be sure to install grub2's boot loader to sdb, so you keep a Windows boot loader in sda.

Gparted uses the boot flag to identify the efi partition, so the boot flag should only be on the efi partition. You can dual boot with Windows in BIOS and Ubuntu in UEFI, but only can choose from UEFI or perhaps one time boot key, not from grub menu. 

UEFI & BIOS are not really compatible and once you start booting in one mode you cannot switch, or once grub is loaded in one mode or the other, you cannot boot any other system in a different boot mode.

Thank you for the info, but like I responded to the previous poster, I would like to keep UEFI. Is there a simple way to do that? Do you know why upgrading to 14.04 from 12.04 messed up what I had working perfectly before?

---

### Post by Dennis N on 2014-10-02
> I would like to keep UEFI. Is there a simple way to do that?

You would have to boot Windows with a different bootloader than Ubuntu's grub. One possibility: Go into the UEFI bios on boot up. You have to interrupt the normal boot to get to the BIOS as I assume you know. Everything depends on how the manufacturer made the UEFI interface, but on mine there is a UEFI boot menu that has entries for what can be booted in either UEFI or BIOS mode. There should be an entry for Windows or at least a listing for the disk Windows is on. I don't need to select a boot mode (Legacy vs. UEFI), it's automatic. Other UEFI may require you to change to Legacy mode first. This would boot into Windows without grub. At least on my UEFI it works that way.

Another way is to install another boot loader like rEFInd. This would give you a single boot menu like grub does. I haven't needed to install it, but here is a link to learn about it:

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by dunn-stephen on 2014-10-02
Hi, thanks for responding. 

> **Dennis N said:**
> You would have to boot Windows with a different bootloader than Ubuntu's grub.

That can't be true, as I mentioned it was working for over a year before I upgraded the other day. Also, chainloading is designed specifically to solve this problem, and grub is capable of doing that. I'm just trying to figure out the simplest way to set this up and understand why it changed at all. 

It seems the newer version of grub that came with trusty is a beta, so I am installing grub2 and trying another route now. Does anyone have any idea what could have caused this?

---

### Post by Dennis N on 2014-10-02
Ubuntu's current UEFI grub cannot boot a system installed in BIOS mode. You must have had the BIOS version of grub previously which would be able to detect and boot Windows. Chainloading transfers the booting to another bootloader other than grub. Good luck with that.

---

### Post by dunn-stephen on 2014-10-02
Well yes, when I wrote "grub is capable of doing that" I meant that grub is capable of transferring to another bootloader. I don't know why it's suddenly UEFI (I wasn't consulted during installation).

---

### Post by Dennis N on 2014-10-02
I agree that if you upgraded (as stated in post #1) and did not do a fresh install, Ubuntu should have remained in BIOS mode. Seems like a bug if it switches. If you did a new install, it's easy to mistakenly select the wrong mode to boot the installer.

Good luck with your manually-created chainloader entry. Do you think we could chainload to grub-pc from grub-efi? That would be interesting, but I doubt it.

---

### Post by oldfred on 2014-10-02
Do you want UEFI or BIOS as boot?
If you want to boot in UEFI mode you must have a boot flag on the efi partition or sdb1. Windows in BIOS mode has to have the boot flag on the partition with bootmgr & BCD. Grub does not use boot flag to boot or chain load to Windows if both are BIOS Mode.

Some of the boot managers that are UEFI, use the UEFI boot once mode to change to BIOS, but you really are then rebooting and choosing a different boot mode to switch from UEFI to BIOS.

I would not change from the default version of grub2. There were a lot of comments where it had many fixes that were needed to work with newer systems.

---

