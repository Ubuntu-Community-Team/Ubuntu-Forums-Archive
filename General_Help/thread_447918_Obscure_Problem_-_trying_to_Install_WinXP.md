---
title: "Obscure Problem - trying to Install WinXP"
date: 2007-05-18
forum: General Help
---

### Post by Tsuki on 2007-05-18
Hi, sorry for the somewhat odd question.  

I'm trying to install WinXP in a spare partition.  However, it only gets as far as "Inspecting your hardware configuration", then goes to a blank screen.  Googled sources suggest this might be due to a corrupt boot sector left behind by a Linux install.  However, it's obviously not *that* corrupt, as I can get into Linux (Ubuntu Feisty) via Grub with no problems.

My question is, is there a non-destructive way of sorting this out from within Linux?  I've fiddled with the partitions in GParted and fdisk as much as I can, and re-written Grub to the MBR, but to no avail.  All the advice I've read on forums so far tends to begin with "wipe your entire hard drive!" which I'm not utterly keen on.

I realise this isn't massively Ubuntu-related, but if any of you have had this experience before, I hope you can give some advice!

Thanks

---

### Post by Cappy on 2007-05-18
Maybe you should use the Windows CD to "fixboot" and "fixmbr". That will remove GRUB. You can reinstall it after Windows installs. I don't have any other ideas =(

---

### Post by S29K on 2007-05-18
The preferred method of dual booting is to install Windows first and then Ubuntu but since you'd rather not have to start from scratch read through the instructions posted by bulldog in this thread

[http://ubuntuforums.org/showthread.php?t=446728&highlight=restore+mbr](http://ubuntuforums.org/showthread.php?t=446728&highlight=restore+mbr)

This should help you out.

---

