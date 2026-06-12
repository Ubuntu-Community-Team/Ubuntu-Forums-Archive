---
title: "Can't Do System Recovery Because of GRUB"
date: 2007-05-16
forum: General Help
---

### Post by Cantabilest on 2007-05-16
Hi, I need some help from experts here in Ubuntu Forums as I'm facing some problems which I consider really serious...

I had a dual-boot system including Windows XP Home and Linux Ubuntu. My laptop actually came with Windows XP Home and then I installed Ubuntu to make it a dual-boot system.

All was well until when I needed to sell this laptop of mine. I decided to perform a System Recovery using the Recovery CDs which came with my laptop during purchase, so that I could return the laptop to factory state and settings, running on only Windows XP Home and with everything in it like a brand new computer.

However, during the process, after I successfully loaded the 2 Recovery CDs and also the Asus Drivers and Utilities CD, problem arose. The pre-installation environment was ready, to install the Windows XP Home I guess. I was prompted to remove all CDs before the computer restarts. But when I did so, there came this error during the restart.

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22

And the screen will stop here forever, until I turn the laptop off by pressing power button. I realised the kernel stuff (which I really don't know much about) has been changed and the process cannot continue without some expert knowledge. Therefore, I'd really appreciate if someone could help me solve this problem, so that I could do the System Recovery on my laptop to return it to brand new state. Thanks lots!!!

I have, since, restarted the laptop and booted from the Ubuntu Live CD and installed Ubuntu again, so now my laptop actually only has 1 OS, Ubuntu.

---

### Post by vtel57 on 2007-05-16
GRUB controls your Master Boot Record on the drive. If you format and reinstall Windows from your factory disks, it should erase GRUB and install its own bootloader on the MBR. I'm surprised it didn't do that when you reinstalled the first time. 

If by chance, it doesn't install the Windows bootloader on your next attempt, just boot to the Windows installation disk and choose Recovery Console at the first menu screen. Once you're in the Recovery Console, which is 100% command line (no graphics), just type fixMBR and hit enter. The Windows disk will install its bootloader on the disk's Master Boot Record and GRUB will be gone forever.

Luck!

---

### Post by Cantabilest on 2007-05-18
hi vtel57, thanks alot for your help!

I'm not formatting with Windows Installation Discs. I'm actually using the Asus Recovery Discs that came with my laptop purchase. As far as I know, it doesn't fully format the harddisk. It will leave behind partitions such as Recovery Partition untouched.

Anyway, there is no "Recovery Console" option given at the beginning. Instead, I have something like this, boot "MS-DOS with CD-ROM Support", which brings me to a black page with white text screen, starting with "A:\", for what I remember. Should I enter the fixMBR in this page? If so, under A:\? or B or C or D:\? E gave an error.

and also I remember vaguely, somewhere in the Recovery process, when I clicked an "Advanced" button, I saw the Bootloader to be something like "hd0". Hope this information helps... helps u to help me. Thanks alot again!

---

### Post by vtel57 on 2007-05-18
Hmm... I don't know how the ASUS recovery disks work. This is why I HATE computer manufacturers who don't give their customers a 100% genuine Windows CD. Heck! You paid for the darn thing! Oh well...

Anyway, yeah... try fixMBR at that DOS prompt. It can't hurt to try. The worst that will happen is that it will say "command not recognized" or something like that.

If it doesn't work, I would recommend perusing ASUS support website to see if there's any help there.

Keep us posted on your progress...

---

### Post by HolyJoe on 2007-05-18
You want to make a **new** machine with window for sell, you sure?!
If so, may be reinstall windows is a better choice, what you think about it?

---

### Post by Cantabilest on 2007-05-20
the fixMBR wasnt recognised in MS-DOS indeed.. gave Asus a call and they told me to bring it down to service centre. Very troublesome. But thanks anyway vtel57. Thanks lots. and Tao, yeah cos i figured buyers would prefer to buy a notebook returned to factory state like brand new... they could install Linux later if they'd like to. ;)

---

### Post by confused57 on 2007-05-20
Here's an excellent guide with several ways to restore  Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)


The Super Grub Disk can also restore the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

