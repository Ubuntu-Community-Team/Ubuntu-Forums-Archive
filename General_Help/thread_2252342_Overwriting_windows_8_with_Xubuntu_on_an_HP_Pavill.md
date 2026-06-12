---
title: "Overwriting windows 8 with Xubuntu on an HP Pavillion DM1"
date: 2014-11-11
forum: General Help
---

### Post by neilajarn on 2014-11-11
I was tasked with installing Xubuntu and overwriting Windows 8 on a HP Pavilion DM1 that was bought from John Lewis.

I spoke to the software support dept at John Lewis who said it should be possible, only first I should make a backup media set of Windows 8 using the HP utility, should anything go wrong it could then be restored to Windows 8. They couldn't/wouldn't give any advice on installing Xubuntu, only wishing me good luck.

I had also been advised to turn off the secure boot in the BIOS. However having had a look in the BIOS, I couldn't see this setting. So then I installed "Belarc advisor" and after a scan it showed that secure boot was already disabled.

When booting from a bootable Xubuntu installation USB the screen flickered and remained that way - a blank flickering screen. I couldn't see a way to get any further than that.

Any advice appreciated.

---

### Post by Topsiho on 2014-11-11
I think the advise to make a backup media set of Windows 8 is a good one. You never know if or when you'll need it, should something go wrong, or you may need it for an other reason.
I am sorry to admit I have no experience installing Ubuntu or one of it's variants on a computer that contains or contained Windows 8.
However, if booting from a bootable Ubuntu or Xubuntu USB stick doesn't succeed, you may try one or more of the options which you'll find under F6 (I think), that you get when booting, and pressing the Space bar (where you can select a language, or find options to test the memory, or some other options. I had to do this on one of my computers, with good success :), and it now runs Ubuntu very well.

Maybe you'll find an option with which the computer boots as it should.

Topsiho

---

### Post by oldfred on 2014-11-11
There are advantages to installing in UEFI boot mode.
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And how you boot installer is how it will install. From UEFI boot menu you should see two menu entries for the Xubuntu installer. One is UEFI and the other is just the label of flash drive or BIOS/CSM.

HP will not easily boot Linux. They have modified UEFI internally to only boot an entry with "Windows" in the description. So we have several work arounds. If not booting Windows you may be able to just change the UEFI entry to read Windows and really be grub's efi boot loader. Others add a copy of grub to the /efi/Boot folder to boot grub as system will still boot from that which is seen as the hard drive UEFI boot entry.

        If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

Other work arounds:
      [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Some other HP:
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by neilajarn on 2014-11-11
Thanks

---

