---
title: "[SOLVED] GRUB is the good guy in a bad fight - help!"
date: 2006-11-29
forum: General Help
---

### Post by seijling on 2006-11-29
In advance I apologize for the long post but it is necessary; as well, I've read for many hours about his issue to no avail.


Lately, I had just installed a fresh copy of Edgy and was liking it a lot.  Also, everything was booting happily and consistently when I decided it wasn't necessary to have two OS selector utilities. (GRUB and Acronis OS selector)

So naturally I removed Acronis and was left with an MBR likened to swiss chesse. It's been 16+ hours of trying to figure out a way to get GRUB to "fix" my mangled MBR.  

Thus far, I have re-installed GRUB after it was mangled by Acronis and it is working for Ubuntu only.  The remainder of listed OS's (Microsoft) are available but only 'partially' unbootable.  To be exact: it lists two different "windows" os's.  I quoted the above because one is a recover partition that will wipe my main partition and the other IS my desired partition.  However, when I select it, it simply hangs. (blinking cursor)

As you can see by the time stamp, its nearly 5AM, and I'm dead if I can't get this computer booted back into Windows soon.  

Please advise and be gentle - I know I'm a noob.   

Mike

PS> the relevant portion of my menu.list/GRUB is as follows:

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by indytim on 2006-11-29
I'd suggest downloading and burning a copy of SuperGrub.  After you've burned the CD, boot to it and let it auto fix your boot situation(s).

Here's the link:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Good Luck,

IndyTim

---

### Post by al_sharpe on 2006-11-30
Hello seijling:

You should want the second windows selection, I believe.

What exactly is the computer doing when you try to boot into

windows.

Your menu.1st looks ok

Wish I could help more, at the moment, will look for 

something. I know nothing about the Acronis loader.

I feel your pain!

Al Sharpe

---

### Post by seijling on 2006-11-30
Well, I figured out what was happening...  And ufourtunately it resulted in the partition/booting information being lost on the Windows Xp portion of the  hard drive.  

As it was, the drive had several bootable sectors: 
1. the Acer recovery (for factory OEM reset) 
2.) Windows XP itself and 
3.) and on onwards were various Linux kernals.  

The problem was that even with direct booting via SuperGRUB (thank you so much **IndyTim**) there was no bootable media on the partition containing windows XP.  A a result no matter how many ways i tried to boot that partition, there just was no information in the MBR to tell the computer how to load.  Acronis had irreperably damaged that section of the MBR and recovery was not possible.  As a last ditch effort I tried the Beta function inside of superGRUB to manually make a partition bootable but it just made the bootable media "not a system disk".

Thankfully none of the partition information in the MBR was lost otherwise I would have lost my data.  I would just like to point out that this was caused by acronis and acronis only - not installing Edgy- in fact before i removed acronis, everything was working grandly.  Just a warning for those thinking of having anything racier than GRUB.  GRUB did have the correct bootloader information, the partition just didn't.  

As a final note - after re-installing the factory OEM, I re-installed GRUB via superdisk so that I could get back into Ubuntu.  Flawless. In fact, it just didn't feel right replying to this in Windows.  ;-)

Either way,  thank you IndyTim and Mr. Sharpe for your help - it really was great to have a friend in a time like that.


Mike

---

### Post by seijling on 2008-03-10
Wow, its weird to read messages from more than a year ago.  Nice to know I haven't gone back either!


Woohoo Gutsy!

---

