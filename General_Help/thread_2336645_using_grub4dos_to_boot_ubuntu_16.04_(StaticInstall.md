---
title: "using grub4dos to boot ubuntu 16.04 (Static/Installed with applications)"
date: 2016-09-10
forum: General Help
---

### Post by wscott66 on 2016-09-10
hello,

[INDENT]I have a fat32 partition on my HDD that has grub4dos on it and I have a number of other tools of this disk that I boot from grub4dos.
I would like to add an installed instance of ubuntu 16.04 to this but cannot figure out what the menu item should look like.
I have 3 partitions on the drive: [/INDENT]
[INDENT=2]1: fat32 grub4dos
2: ext4 / (root)
3: swap[/INDENT]
[INDENT]
Greatly appreciate any help i can get to make this work...[/INDENT]

Thanks in advance!
Bill S.

---

### Post by Jimysbil on 2016-09-10
I assume you are talking about an installed version of ubuntu (not an iso).
Practically you can boot an installed system like this:
```
title Ubuntu 16.04
fallback 3
root (hd[COLOR=#FF0000]{disk number}[/COLOR],[COLOR=#ff0000]{partition number}[/COLOR])
kernel /boot/vmlinuz-4.4.0-36-generic root=/dev/sd[COLOR=#ff0000]XX[/COLOR] ro
initrd /boot/initrd.img-4.4.0-36-generic
boot
```

But I think it does not worth the effort as long as ubuntu is upgrading the kernels and you have to add them manually to *menu.lst*.

So why don't you install grub bootloader in order your installed OS has complete control of it?
It also will regenerate the configuration by itself when it's needed.
If you have other entries into your grub4dos menu.lst and you don't want to transfer all of them to your grub, you could add an entry of your grub4dos bootloader to your grub 40_custom configuration file in order you be able to switch bootloaders.

In case you want to boot an iso image with grub4dos check [here]("http://askubuntu.com/questions/771152/using-grub4dos-to-boot-ubuntu-16-04").

---

### Post by wscott66 on 2016-09-10
Can I put and entry in the grub4dos  menu to point at the Ubuntu grub? 
That way bypassing having to update the entry are the kernel is updated.

---

### Post by Jimysbil on 2016-09-10
I think you can do that by adding to *menu.lst*:
```
title Load Grub2
find --set-root /boot/grub/core.img
kernel (hd[COLOR=#FF0000]{disk number}[/COLOR],[COLOR=#ff0000]{partition number}[/COLOR])/boot/grub/i386-pc/core.img
```

You could also use this format in order to load the boot code on a specific partition:
```
title Chainload Grub2
chainloader (hd[COLOR=#FF0000]{disk number}[/COLOR],[COLOR=#ff0000]{partition number}[/COLOR])+1
```

---

