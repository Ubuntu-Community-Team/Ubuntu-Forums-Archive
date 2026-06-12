---
title: "Grub won't boot"
date: 2019-04-23
forum: General Help
---

### Post by beegie2 on 2019-04-23
Hello,
I have a problem that appeared 2 weeks ago: grub won't boot automatically and shows grub command line instead. I have to set it up manually in order to boot with the following commands:

```
$ set root=(hd0,gpt2)
$ linux /vmlinuz root=/dev/sda2
$ initrd /initrd.img
$ boot
```

It came out of nowhere. I don't remember doing anything that could have caused that.
I tried some stuff to fix this like boot-repair, update-grub, change BIOS order...

Here is the pastebin from boot-repair : [https://paste.ubuntu.com/p/92qYQM8Cgn/](https://paste.ubuntu.com/p/92qYQM8Cgn/)

FYI, I installed debian before switching to ubuntu. I don't think the problem is around this since it worked like a charm for ~1 month.

I could do a fresh install of ubuntu which would probably fix this, but I am also interested in knowing what is the problem here. I am not good enough to fix this by myself so I could use some help here.

---

### Post by iamtheeggman2 on 2019-04-23
I used a program called boot-repair it has a gui so it is easy to use. Though it has an automated Repair feature some on here recommended against its use. Anyway its easy to use give it a try.

---

### Post by oldfred on 2019-04-23
It shows 25_custom which is only created by Boot-Repair for added UEFI boot entries in grub menu.
Most can turn off execute bit on that file, to remove those entries from grub menu. Or edit entries for just those you may want.

It looks like it did a full reinstall of grub, not just the update of grub. And it set Ubuntu as first in boot order.
Does it now work?
You showed before Debian as default boot, which would give a grub terminal. You may want to remove Debian UEFI entries in NVRAM with efibootmgr & remove /EFI/Debian folder in ESP - efi system partition.

You show both Intel & nVidia for video.
Once it boots which are you using?

---

### Post by beegie2 on 2019-04-26
> **iamtheeggman2 said:**
> I used a program called boot-repair it has a gui so it is easy to use. Though it has an automated Repair feature some on here recommended against its use. Anyway its easy to use give it a try.

Well that's what I used to try to fix it :)


> **oldfred said:**
> It shows 25_custom which is only created by Boot-Repair for added UEFI boot entries in grub menu.
Most can turn off execute bit on that file, to remove those entries from grub menu. Or edit entries for just those you may want.

It looks like it did a full reinstall of grub, not just the update of grub. And it set Ubuntu as first in boot order.
Does it now work?
You showed before Debian as default boot, which would give a grub  terminal. You may want to remove Debian UEFI entries in NVRAM with  efibootmgr & remove /EFI/Debian folder in ESP - efi system  partition.

You show both Intel & nVidia for video.
Once it boots which are you using?

That's it! I removed the debian entry with efibootmgr and now it boots on ubuntu directly :) Thanks! 
Though, it is weird that the boot was working properly for about ~1 month and started to boot on debian entry all of sudden.
As for the graphic drivers, it uses nVidia I guess. Should I uninstall Intel drivers?

---

### Post by oldfred on 2019-04-26
On my system with nVidia, I do not uninstall Intel drivers.

You can check if installed into kernel:
       dkms status

---

