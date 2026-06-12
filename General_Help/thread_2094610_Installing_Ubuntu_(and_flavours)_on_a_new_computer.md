---
title: "Installing Ubuntu (and flavours) on a new computer with Windows 8"
date: 2012-12-14
forum: General Help
---

### Post by COMECON on 2012-12-14
Hi all,
I'm planning to buy a new computer, a Dell XPS 8500, which comes with Windows 8. I read a bit about it, and it seems like installing Linux on Windows 8 computers may give me problems, due to EFI, UEFI and other things that aren't compatible with GRUB or something like that...
Could somebody explain it to me, and if it's possible to install Linux as always has been done on a "new" Windows 8 computer?

Catbuntu

---

### Post by ezeze5000 on 2012-12-14
In order to install Ubuntu on a windows 8 computer you have to go into
the BIOS F2 usually. Look for the boot tab select boot order, then look for the UEFI secure boot and disable it. then reboot and Ubuntu will install normally. I hope this will help you.

---

### Post by grahammechanical on 2012-12-14
The first thing you can do is use Ubuntu 12.10. It comes with a kernel that has been signed with a Microsoft security key. This will deal with the secure boot issue.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

But be prepared for problems. Note this:

> The Ubuntu first-stage EFI bootloader is signed by Microsoft, but the key that is used for signing is one that's recommended by Microsoft, not one that's required by the Windows 8 certification requirements. Will all hardware include this key in practice

The second thing that you should accept is that in trying to do this, you become an experimenter. There are several threads on this forum about people trying to do this. The answers are not yet complete.

Here are 2 examples:

[http://ubuntuforums.org/showthread.php?t=2093362]("http://ubuntuforums.org/showthread.php?t=2093362")

[http://ubuntuforums.org/showthread.php?t=2090970]("http://ubuntuforums.org/showthread.php?t=2090970")

My advice would be to proceed with caution and study what steps you have to do to fix things if things go wrong. Remember, hardware makers only care about getting Windows 8 working acceptably on their machines. They are not interested in abiding by standards that would make a linux install more successful.

Regards.

---

### Post by Mark Phelps on 2012-12-14
If you decide to dual-boot, not to wipe Win8, then be SURE to use the Win8 Disk Management utility to shrink the Win8 OS partition to make room for Ubuntu.

Using the Ubuntu installer, or GParted, runs the risk of corrupting the Win8 filesystem -- which will then render it unbootable.

---

### Post by coffeecat on 2012-12-14
@COMECON, this community documentation page may be useful to you:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2012-12-14
One user with Dell worked after some effort.

       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

Most systems also need a setting called fast boot or quick boot turned off. Some systems have worked with secure boot on, some with it turned off and some have UEFI that have bugs.

---

### Post by COMECON on 2012-12-14
Thanks to all the replies,
I think I won't be really using Windows 8, so I can (and maybe preffer) formating the entire disk, installing Ubuntu or whatever, and then my old Windows 7. 
If I do this, will I have to do any extra steps too, or will all the "UEFI problems" disappear after formating?

Catbuntu

---

### Post by oldfred on 2012-12-14
I thought there might be Windows driver issues. Windows 8 are new systems that have newer drivers and I think I saw where they said they would not provide drivers for Windows 7. I am sure to make you stay with Windows 8. Plus your Windows 7 was only licensed for one system, so you would need a new copy.

The UEFI/BIOS supposedly can revert to BIOS mode. Have not seen anyone do that with a Windows 8 system, but some have installed Ubuntu in BIOS mode on Windows, but then had to convert to UEFI mode to be able to dual boot.

You also then are back to MBR(msdos) 4 primary partition limit as Windows only boots from gpt partitioned drives with UEFI. Ubuntu can boot from gpt with BIOS or UEFI or MBR with with BIOS.

---

