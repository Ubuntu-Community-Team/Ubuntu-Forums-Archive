---
title: "Help needed in configuring dual boot system"
date: 2004-12-07
forum: General Help
---

### Post by ryan on 2004-12-07
I am running a dual boot system :

2 Hard drives both 80 gigs

hd 0 formerly XP Pro

hd1 FC3 where grub resides

I want install Ubuntu in place of XP on hd0 but I want my current grub with FC3 to handle the boot process.

Since hd 0 will be where Ubuntu will be installed I am concerned that the grub that is installed there won't find my old grub.  Will the grub on hd 0 find the grub on hd1 ?

My current grub:

timeout=10
splashimage=(hd1,1)/grub/splash.xpm.gz
title Fedora Core (2.6.9-1.681_FC3)
root (hd1,1)
kernel /vmlinuz-2.6.9-1.681_FC3 ro root=LABEL=/ rhgb quiet
initrd /initrd-2.6.9-1.681_FC3.img
title Fedora Core (2.6.9-1.678_FC3)
root (hd1,1)
kernel /vmlinuz-2.6.9-1.678_FC3 ro root=LABEL=/ rhgb quiet
initrd /initrd-2.6.9-1.678_FC3.img
title Fedora Core (2.6.9-1.667)
root (hd1,1)
kernel /vmlinuz-2.6.9-1.667 ro root=LABEL=/ rhgb quiet
initrd /initrd-2.6.9-1.667.img
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +

It was suggested that do any of the following any perferences pros cons ?

1) When your installing Ubuntu make sure that you don't install a bootloader. Then you'll want to edit the grub configuration by hand and add the Ubuntu entries.

2) If you boot from second disk (FC3), you don't need to change anything. Selecting the "Windows" entry in your bootloader menu would boot first disk (Ubuntu). You can rename the entry to read "Ubuntu" instead of "Windows". Like this:
title Ubuntu
rootnoverify (hd0,0)
makeactive
chainloader +

3) If you boot from first disk (Ubuntu), you need to add a bootloader entry to chainload your bootloader in MBR of second disk. For GRUB that would be:

title Fedora Core 3
rootnoverify (hd1,0)
makeactive
chainloader +1


tks any input appreciated..

---

