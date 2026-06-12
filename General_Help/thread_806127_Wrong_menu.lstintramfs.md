---
title: "Wrong menu.lst/intramfs"
date: 2008-05-24
forum: General Help
---

### Post by ezramorris on 2008-05-24
Hi, trying to install Wubi on a PC running WinXP. The install completes successfully, but then the following happens:

I reboot and choose Ubuntu.
Then a grub boot menu appears, but this has a load of options for Topologilinux (a Wubi-like distro which I had installed at one point, but then removed it).
So I press c and type
```
find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
 (hd0,1)
 Filesystem type is ntfs, partition type 0x7
configfile /ubuntu/install/boot/grub/menu.lst
 Press esc to enter the menu [54321]
```
I then get the Ubuntu splash screen with a bouncing bar which lasts for about 2 minutes, followed by a flashing cursor for about 1 minute, then the system drops to an (initramfs) prompt.

Pressing ctrl-alt-f1 doesn't show anything useful, just

```
Loading, please wait...
```

Any ideas of what the problem(s) are/is?

Thanks in advance

---

### Post by ago on 2008-05-24
See if any of those helps:
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

### Post by ezramorris on 2008-05-27
> **ago said:**
> See if any of those helps:
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

Hi,
Thanks. I had a look at that and tried the steps it suggested. All I managed to do was speed up booting to initramfs. So, I gave up. I think I might do a full install/dual boot. However, now I have the problem of Windows putting unmovable files at the end of the drive.

Thanks again.

---

