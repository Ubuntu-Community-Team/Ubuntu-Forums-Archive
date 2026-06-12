---
title: "Ubuntu Uninstall Leaves Boot Entry?"
date: 2008-04-30
forum: General Help
---

### Post by AStaley on 2008-04-30
I've had Ubuntu+Kubuntu installed on my computer both with entries in the boot menu when I startup.  I've since uninstalled both versions, but still have the entries left?

How do I modify the boot menu to boot straight into Vista?

At somepoint I intend to restore Ubuntu my system, but I don't want the double/triple entries.

Thanks in advance, AStaley.

---

### Post by ibutho on 2008-04-30
Use the [super grub disk]("http://www.supergrubdisk.org/") to remove grub and restor the Windows bootloader.

---

### Post by ago on 2008-04-30
EasyBCD is excellent to edit the Vista menu without having to change the bootloader. 

I am not sure though how you ended up with 2 entries to begin with. Are they using the same version of wubi (8.04). Or were they on different versions?

---

### Post by pastalavista on 2008-04-30
Boot from your Windows install disk and choose the repair option. At the DOS prompt type: [fix boot] or [fixmbr] (without the brackets)

---

