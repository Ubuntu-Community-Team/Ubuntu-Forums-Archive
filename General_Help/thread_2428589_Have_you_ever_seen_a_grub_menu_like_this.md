---
title: "Have you ever seen a grub menu like this?"
date: 2019-10-06
forum: General Help
---

### Post by MibunoOokami on 2019-10-06
Hi all,

Have you ever seen a grub menu that looks like this?
```

Ubuntu
Advanced options for Ubuntu
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
Windows Boot UEFI fbx64.efi
EFI/ubuntu/fwupx64.efi
EFI/ubuntu/mmx64.efi
EFI/BOOT/bkpbootx64.efi
EFI/BOOT/fbx64.efi
EFI/ubuntu/mmx64.efi
Windows Boot Manager
System setup
```

That is what appears on an old acquaintance’s computer, who isn’t bothered by it unless it is the cause of very sluggish performance and regular bouts of freezing. 

I thought I'd make a post about this because I’m quite curious about it, as I don’t recall ever seeing anything like that before, and just want to know what, if anything you can tell me about it?
All my attempted searches keep resulting in how to fix a broken/missing grub, which is not helpful since I don’t think this is broken.

---

### Post by Dennis N on 2019-10-06
The additional entries are introduced by using boot repair. They can be removed by making **/etc/grub.d/25_custom** non-executable, and then running sudo update-grub.

---

