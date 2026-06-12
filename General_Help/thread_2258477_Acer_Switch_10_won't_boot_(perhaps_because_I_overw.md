---
title: "Acer Switch 10 won't boot (perhaps because I overwrote on the windows boot partition)"
date: 2014-12-28
forum: General Help
---

### Post by mokawi2 on 2014-12-28
Hi,

I tried to install Ubuntu 14.10 on my Acer Switch 10 (SW5-012).

I managed to have the installer launch by building bootia32.efi from grub2 and putting it on the installer usb key (this is normal, Bay Trail computers apparently neet a 32bit bootloader...). I installed Ubuntu alright (well, kinda—wifi and keyboard doesn't work out of the box), but I had the whole drive repartitionned and reformated, so I lost the windows boot partition. Perhaps as a result, it doesn't boot (drive not detected).

I tried various things:
[LIST]
[*]put bootia32.efi in /efi/ubuntu/ in the boot partition 
[*]copy everything in /efi/ubuntu/ to /efi/boot/ 
[*]copy everything in /efi/boot/ to /efi/Microsoft/Boot 
[*]register /efi/ubuntu/bootia32.efi using efibootmgr (installed on the installer disk using apt-get) 
[/LIST]

Nothing works. It still cannot detect the bootloader.

Any idea as to how I could fix this mess?

Thanks!

Louis

---

### Post by ajgreeny on 2014-12-28
Did you actually make a small (100 - 200MB) fat32 partition and use it as efi when making the partitions while you were installing Ubuntu?  You do not need a separate /boot partition, in fact I would suggest it is best not to have one unless using encryption or LVM, which will make a /boot partition for you, but it is essential to have the efi partition.

Are all your partitions using a gpt partition table?

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for lots of detailed info.

---

### Post by mokawi2 on 2014-12-29
The Ubuntu installer made such a partition, and it is mounted on /boot/efi (when I manage to boot the os from the usb key's grub shell). Also, all partitions are using gpt.

Thanks for the link. I reinstalled ubuntu with the instructions for [32bit grub installation]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md"). It failed, so I tried to fix it with boot-repair, and it failed to repair it. From the [paste it created]("http://paste.ubuntu.com/9638457/"), I think it tried to put a new 64bit bootloader (shimx64.efi), which is obviously a bad idea.

I guess I would have to restore the 32bit grub and register it with efibootmgr. But then again, that's what I did last time... I must've done it wrong.

I'll keep trying stuff and posting it here, but I'll gladly take new suggestions.

---

### Post by ajgreeny on 2014-12-29
I am not an expert in grub, but why do you need the 32bit packages; are you trying to install a 32bit OS?

---

