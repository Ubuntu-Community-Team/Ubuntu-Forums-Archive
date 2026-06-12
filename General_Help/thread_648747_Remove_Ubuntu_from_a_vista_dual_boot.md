---
title: "Remove Ubuntu from a vista dual boot"
date: 2007-12-24
forum: General Help
---

### Post by mustermania on 2007-12-24
Hello all,

I've been running vista and ubuntu 7.10, but I need to need to switch to a vista and suse dual boot.  I can't figure out how to fix the vista MBR and get my ubuntu partion space back.  Anybody come across a fix?

---

### Post by dondad on 2007-12-24
Not sure about Vista as I haven't played with it much, but with XP, you could boot the Windows install disk, choose the recovery console option and type "fixmbr" (without the quotes). This would overwrite the grub entry in the mbr with the Windows version. After that, you can do whatever you need to with the partitions.

---

### Post by fain on 2007-12-24
> **mustermania said:**
> Hello all,

I've been running vista and ubuntu 7.10, but I need to need to switch to a vista and suse dual boot.  I can't figure out how to fix the vista MBR and get my ubuntu partion space back.  Anybody come across a fix?

Why don't you just try and install SUSE over top of Ubuntu. I mean just have the suse installer delete the Ubuntu partition. It will install Suse's boot loader over Ubuntu's boot loader.

---

