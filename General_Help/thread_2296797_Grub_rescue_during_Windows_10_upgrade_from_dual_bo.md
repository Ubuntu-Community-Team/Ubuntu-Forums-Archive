---
title: "Grub rescue during Windows 10 upgrade from dual boot"
date: 2015-09-28
forum: General Help
---

### Post by Joseph_Hui on 2015-09-28
Hi folks,

I've been dual booting Windows 7 and Ubuntu, accessing whichever one I wanted to use with the grub prompt. I upgraded from Windows 7 to Windows 10, and during the upgrade process, my computer restarted and presented me with a grub rescue prompt. I tried to restore Grub with a LiveUSB, but it didn't seem to do anything: the paste is [here]("http://paste.ubuntu.com/12607774/"). My PC still boots into grub rescue with no apparent way to get to either Windows or Ubuntu.

I have three physical drives: a 500GB hard drive (on which Windows/Ubuntu reside), a 1TB hybrid drive, and a 500GB SSD. Looking at gparted, I believe these correspond to sdc, sda, and sdb respectively, with sdc3 being the boot partition.

Ideally I would like to end up booting into just Windows 7 or 10 and remove Ubuntu entirely (I have a separate machine that I run Ubuntu on). If I understand correctly this would entail restoring the Windows MBR. However, just fixing grub would work too. It seems like this may be possible by making a Windows recovery CD, as [this thread]("http://ubuntuforums.org/showthread.php?t=1335353") mentions; however, I don't have any writeable CDs at the moment (though I could buy some). I've tried some elaborate methods of making a Windows recovery USB but they don't seem to work correctly; even if I boot into the USB from my BIOS, it just ignores it and moves on to grub-rescue.

I don't really have any data of value on either Windows or Ubuntu, so solutions that might cause data loss are fine, as long as I can eventually get to a working Windows installation.

Any ideas?

Thanks!

EDIT: I was able to get my hands on a Windows repair disk, and was able to fix the problem using that. If anyone happens to run into this exact scenario, I fixed it by using bootrec.exe and basically trying a bunch of different commands until it worked out.

---

