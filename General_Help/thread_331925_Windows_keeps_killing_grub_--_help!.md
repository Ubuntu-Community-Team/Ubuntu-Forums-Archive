---
title: "Windows keeps killing grub -- help!"
date: 2007-01-05
forum: General Help
---

### Post by Kensey on 2007-01-05
I have three dual-boot systems.  One (work desktop) is XP Pro/Edgy on a SATA hard drive, one (personal laptop) is XP Pro/Dapper on a SATA hard drive, and one (home desktop) is XP Pro/Edgy on an IDE hard drive.

The laptop and the home desktop have given me no issues.  However, the work desktop (a Dell Optiplex GX620) has been nothing but trouble.  The preferred mode is to have the default OS be Windows, and leave it booted to Windows while idle so system management (updates and automated installs) can take place.  However, after awhile booted to Windows, if I reboot, Grub is broken and the computer goes into an infinite cycle of Grub errors (looks like a stage 1.5 load error, but it goes away too fast to read) followed by immediate reboots.

I Googled and found this is fairly common, and the recommended fix is apparently to delete the stage 1.5 files in /boot/grub and reinstall grub to the MBR (I don't know why this would fix it, since that was how it was installed originally, but it seems to work for some people).  However, I've done that and I still have the same issue.  I tried reinstalling to both hd0 and hd0,2 (/ is /dev/sda3 on this drive).  Installing to hd0 fixes the problem (until the next time), installing to hd0,2 doesn't.

If I had to guess, something is running periodically in Windows and trying to "fix" a bootloader it sees as "broken".  I saw a forum thread in which someone suggested that Microsoft's Malicious Software Removal Tool is the culprit, but there's no interface to MSRT in Windows.  So:

[list=1]
[*] Is MSRT known to break dual-boot in this way?
[*] If so, is there a way (through the registry or otherwise) to tell it to stop messing with the boot sector?
[*] If MSRT is the culprit and can't be politely told to go throttle itself, can it be uninstalled?  (We run Symantec AV in a managed environment here, I doubt MSRT really does anything for us.)
[*] Assuming MSRT is untouchable, can the bootloader be protected on the hardware level somehow?  The disk is a Samsung HD080HJ/P.
[/list]

---

### Post by Mithrilhall on 2007-01-05
Have you removed the Microsoft tool?

[http://support.microsoft.com/kb/890830](http://support.microsoft.com/kb/890830)

---

### Post by scrooge_74 on 2007-01-05
Maybe this will help

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Kensey on 2007-01-05
> **scrooge_74 said:**
> Maybe this will help

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hey, that actually looks like something that will keep Windows happy.  Much as I hate using MS when Linux has better tools, in this case maybe if I feed Windows what it wants I can finally live in peace.  Thanks!

Once I do that, will I get a Windows boot menu and then a Grub boot menu also?  (If so, I can just set the default grub boot to Ubuntu and the delay to zero, I'm just curious.)

(Edit: I'm using a link somebody posted in that thread that details how to set up Windows' bootloader to boot a Linux partition.)

---

