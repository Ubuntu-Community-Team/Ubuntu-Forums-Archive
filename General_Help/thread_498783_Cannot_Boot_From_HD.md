---
title: "Cannot Boot From HD"
date: 2007-07-11
forum: General Help
---

### Post by lakelovers on 2007-07-11
My montior went south a month ago and I just got it back. Now, I cannot boot from the HD. It worked fine for the few years I've been using Ubuntu. So I can't imagine what has changed. I have the bios seeing the HD as the first boot device, but when I start up the computer I'm asked to insert a bootable CD. Which I do and Ubuntu loads fine. Any ideas why I can't boot directly from the HD? I don't use a dual boot. Ubuntu is my only OS.

---

### Post by confused57 on 2007-07-11
> **lakelovers said:**
> My montior went south a month ago and I just got it back. Now, I cannot boot from the HD. It worked fine for the few years I've been using Ubuntu. So I can't imagine what has changed. I have the bios seeing the HD as the first boot device, but when I start up the computer I'm asked to insert a bootable CD. Which I do and Ubuntu loads fine. Any ideas why I can't boot directly from the HD? I don't use a dual boot. Ubuntu is my only OS.
You might try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by lakelovers on 2007-07-12
Well, I tried re-installed grub via the link you gave me and screwed up. I now have a live CD booted and trying again to go thru the instructions. I ran into a problem right off. The terminal doesn't doesn't recognize "grub," or I don't know how to get to the grub.  I'm using live CD version 5.04, which is the only one I have. How do I handle this? Or, is the live CD too old? Hope you or somebody can get me out of this hole.

When I do a search for "grub" I get:

boot-grub.pl  /user/share/setup-too-backend/scripts

---

### Post by confused57 on 2007-07-12
I would think the 5.04 live cd would work to reinstall grub...you might be able to install grub by booting into your installation and trying
```
sudo grub-install /dev/hda
```
if your hard drive is designated as hda.

If this doesn't work and you have a copy of the 5.04 alternate install cd, you might try this:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

I don't know if doing a filesystem check would help or not:
[http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check](http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check)
the gparted live cd is probably the easiest way to do this.

---

### Post by lakelovers on 2007-07-13
I'm back up running after reinstalling GRUB from a "Super GRUB" CD that I forgot I had. Unfortunately that didn't solve the initial problem of having to boot from a system disk. I'm a bit nervous about running the install CD because the jacket says it will wipe out the HD before installing. I've forgotten whether there's a menu on the install CD. I'm beginning to wonder if I have a BIOS problem. I've checked it a couple of times and the HD is designated as the first option for booting. Where do I go from here?

---

### Post by confused57 on 2007-07-13
It definitely sounds like it could be a bios problem....you might make a note of the exact error message and see if a Google search turns up anything, which you may have already done.   I don't know if setting your bios to default settings or possibly a failsafe mode would help or not.

I wouldn't think your mbr would cause this error, but maybe you can find something to try in this guide:
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

---

### Post by lakelovers on 2007-07-13
I'm baffled. I reset the Bios drive order to the default, which put the disk drive first, HD second, CD third. and with Hard Drive Priority. I restarted the computer. Same thing: I'm asked for a boot cd. When I put the CD in, I'm given the choice of selecting the HD or CD. I select the HD and Ubuntu loads. I know I can leave the CD in all the time and select the HD, but that ain't right. There's probably a simple solution around some place. This situation is more of a nuisance than a problem. I've been thinking about upgrading to the next version of Ubuntu. Maybe that would fix the problem . . . of give me more problems.

---

### Post by dagnabit dang doohickey on 2007-07-13
This howto may be helpful: [How to restore Grub from a live Ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by yorkie on 2007-07-13
Just a quick question what happens if you don`t put a disk in  when it ask for a boot disk does system just hang waiting for a disk?.
have you tried just pressing enter.

---

### Post by lakelovers on 2007-07-16
Yes, it hangs. I get the message: Boot Device Detected. Insert System Disk and Press F1. When I press F1, I get these options: Boot from Hard Drive; Boot from CD-Rom. I select the first option booting from the hard drive and Ubuntu loads. It also has a timer that will auto boot from the hard drive in X seconds.

---

