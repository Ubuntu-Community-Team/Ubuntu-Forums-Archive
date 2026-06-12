---
title: "A few questions on GRUB and boot loaders."
date: 2008-04-10
forum: General Help
---

### Post by nappymonster on 2008-04-10
Hi all,
Whereas Grub sort of does what i need it to do (Boot into ubuntu, boot into vista), there are some problems i have with it:

-It occasionally gives me error 21.
-It's not 'Pretty'
-It put itself on the internal hard drive, not external, where ubuntu is stored.

So:
-How do i put GRUB on my external hard drive
-Can i make grub more graphical?
-What are some other boot loaders?
-Which do you think i should use?
-How do i 'transfer' bootloaders (E.G change from GRUB to something else)?

Thanks,
Nappymonster

---

### Post by confused57 on 2008-04-10
You can use a Vista install DVD(not a recovery disk) to install Vista's IPL(Initial Program Loader) to the internal drive's mbr, using bootrec.exe:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you don't have a Vista DVD, Super Grub Disk can also do this:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If your bios is capable of booting first to your external hard drive, you can install grub's IPL to it's mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
something like:
```
sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit
```

Then boot first to your external drive, if you get a grub boot menu, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, then change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot.  This is temporary if it works, but you can make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```

Another option is using EasyBCD, which will allow you to boot Ubuntu from Vista's bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
You would need to then use the Ubuntu live cd to install grub to the root partition, rather than to the external drive's mbr, e.g.
```
sudo grub
find /boot/grub/stage1
```
use the output of the above, then:
```
root (hdx,y)
setup (hdx,y)
quit
```

---

