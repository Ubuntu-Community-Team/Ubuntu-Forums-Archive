---
title: "Removing Ubuntu"
date: 2007-01-26
forum: General Help
---

### Post by sNNooPY on 2007-01-26
I've got 2 hard drives. WinXP is on my first drive and I've installed Ubuntu on the second drive.
I want to unistall ubuntu. The problem is: GRUB is installed on the first drive.
When I deleted ubuntu partitions (/ & swap) via Acronis Disk Director from WinXP, computer woudn't boot : GRUB showed error 15 so I reinstalled ubuntu just to get to Windows.
How can I safely unistall ubuntu & GRUB?

Thank you

---

### Post by Ramses de Norre on 2007-01-26
Boot your windows cdrom, go to the rescue prompt and type in this:
```
fixboot
fixmbr
exit
```
Now grub should be replaced by the original windows bootloader again.
If it doesn't work you might need to swap the first two commands, I'm not sure in which order you need to execute them.

Why didn't you like ubuntu?

---

### Post by sNNooPY on 2007-01-26
> **Ramses de Norre said:**
> Boot your windows cdrom, go to the rescue prompt and type in this:
```
fixboot
fixmbr
exit
```
can't do this.
I've got ASUS P5B Deluxe, hard drives are set in AHCI mode and FIXMBR warned me that I have "unusual drive setting" or something like that and that it can mess up my partition which is NOT an option. :)
I have to figure that one out...
> **Ramses de Norre said:**
> Why didn't you like ubuntu?
I like Ubuntu, but I installed the wrong version (32bit instead of 64bit), and I have to reorganize my partitions.

---

