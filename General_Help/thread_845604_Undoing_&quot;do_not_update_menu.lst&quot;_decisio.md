---
title: "Undoing &quot;do not update menu.lst&quot; decision after kernel update?"
date: 2008-06-30
forum: General Help
---

### Post by Manad on 2008-06-30
I clicked the wrong thing at some point while installing the package updates. Basically the Kubuntu update manager gave me a choice between updating Grub's menu.lst, or leave the old one. I selected the latter, and as a result I'm not booting the latest kernel.

I tried manually editing menu.lst and copy/pasted the 2.6.24-17 (the kernel I currently load) so I could have this:
title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=242da-a4a9-4259-8727-1ebc7c56f4a6 ro single
initrd		/initrd.img-2.6.24-17-generic

But this doesn't finish booting.

I also tried reinstalling the -19 image in Adept, hoping I would be asked again, but I wasn't.

Any ideas?

---

### Post by plucky on 2008-06-30
> **Manad said:**
> I clicked the wrong thing at some point while installing the package updates. Basically the Kubuntu update manager gave me a choice between updating Grub's menu.lst, or leave the old one. I selected the latter, and as a result I'm not booting the latest kernel.

I tried manually editing menu.lst and copy/pasted the 2.6.24-17 (the kernel I currently load) so I could have this:
title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=242da-a4a9-4259-8727-1ebc7c56f4a6 ro single
initrd		/initrd.img-2.6.24-17-generic

But this doesn't finish booting.

I also tried reinstalling the -19 image in Adept, hoping I would be asked again, but I wasn't.

Any ideas?

You are editing the recovery mode kernel boot line,you need to edit the full boot mode line and should look like this

```
title		Kubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=242da-a4a9-4259-8727-1ebc7c56f4a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

Good Luck

---

