---
title: "Grub Error and External Hard Drive"
date: 2008-04-03
forum: General Help
---

### Post by poximex on 2008-04-03
Hey everyone,

I am a complete beginner to Linux, so I'm pretty ignorant when I come across an error. I read some similar threads, but some of the solutions seemed over my head.

My story started when I needed to install Linux on a computer so I could do coding for a design project class. I installed 7.10 (I had to use the alternate CD) on a 250GB Western Digital drive I have in an external enclosure. However, because of some rather strange issues with the video resolution (my Quadro video card would only run at 640x480), I decided tonight to install 8.04. The installation went fine, and I can load it successfully.

My main problem comes with booting. I have Vista on the laptop hard drive right now, and would rather use it until I become more comfortable with Linux. With 7.10, if I didn't have the external hard drive present, or simply off, it would auto-boot into Vista - no boot seletor. If the hard drive was on, I could select which version of Linux I wanted (memtest, recovery, etc) However with 8.04, I need to have the hard drive here and on, otherwise I get a **GRUB Error 21**. I googled the error, and it basically means it can't find the drive.  I'm not in my room very much and it isn't practical for me to carry around this external hard drive. Vista crashes (thus Linux, right?).... software needs restarts.... the list goes on, but I need some way to get back into Vista if my machine gets powered off.

I am 99.9% certain that grub was probably installed on the external hard drive, so thats why I need the external hard drive to boot. I need a way to either 1) change the settings to autoboot Windows with no external hard drive like in 7.10 (USB HDD has BIOS priority over HDD0), or 2) get GRUB on HDD0 so I can at least boot windows.

Thanks for your help guys. I'm not familiar with editing boot records, terminal commands, etc, so I figure this is a good time to learn.

---

### Post by confused57 on 2008-04-04
This should explain grub error 21 & what may have happened:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

If you have a Vista install DVD, you can use the bootrec.exe utility to restore your Vista IPL to the internal hard drive's mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you don't have a Vistal install disk, you can use Super Grub Disk to do this:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

There's also MbrFix.exe:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Once you're able to boot your internal hard drive without grub, then you can install grub to the external drive's mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
"find /boot/grub/stage1" will probably return something like "root (hd1,0)", you would need to:
```
root (hd1,0)
setup (hd1)
```

This "should" give you a grub boot menu when you boot first to your external drive, but you will need to change the root to (hd0,0)...you can do this by highlighting your Ubuntu entry in the grub boot menu, press "e", select the line with root, press "e" again, then change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.  This is temporary if it works, but you can make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```
you also need to change the line with #groot to (hd0,0)...leave the #  in front of groot.

---

