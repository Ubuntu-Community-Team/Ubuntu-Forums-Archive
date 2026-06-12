---
title: "Computer automatically boots to Windows without grub showing up."
date: 2015-07-10
forum: General Help
---

### Post by Amanda_Daly on 2015-07-10
I finally got Ubuntu 14.04 installed and working but every time I turn on my computer it automatically boots to Windows 8.1. I can access Ubuntu by entering the boot manager (pressing esc on startup then F9 for boot options), but this fix is only temporary. I have tried using boot repair and various things I've found around the internet to try and solve this problem myself but I can't. The boot repair logs can be found [here]("http://paste.ubuntu.com/11858726/") and it would be wonderful to find a solution to this problem. Thanks!

---

### Post by Irihapeti on 2015-07-10
*Thread moved to **General Help**.*

Resolution Centre is for issues with your forum account.

---

### Post by oldfred on 2015-07-10
HP's need work arounds, and Boot-Repair often adds many grub menu items which you may want to clean up. All those details are in link in my signature.
HP is one of the vendors that modifies UEFI to also use description. And only allowed description in UEFI menu that is allowed to boot is "Windows". That is not allowed per UEFI standard.

Most with HP use either Boot-Repairs suggestion of entry to BCD with Windows,and/or rename of bootx64.efi and booting the hard drive or fallback boot entry.

Others that have gotten HP to work.
       HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

[URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

