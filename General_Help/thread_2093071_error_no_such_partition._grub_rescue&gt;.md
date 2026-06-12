---
title: "error: no such partition. grub rescue&gt;"
date: 2012-12-09
forum: General Help
---

### Post by ctg867 on 2012-12-09
When doing a clean install of Windows 7 on my laptop, I put aside a 20GB partition so I could dual boot Ubuntu 12.10. The install worked fine, but instead of extending my already short battery life for basic programs, Ubuntu actually drained it dramatically faster.

After trying and failing to resolve the issue and thus finding no purpose for Ubuntu in my daily computer use, I decided to remove it. From within Windows, I used the Disk Manager to remove the Ubuntu partition, and reintegrate it back into my Windows partition. It worked fine, but the next time I booted my computer up, I got the following message:

error: no such partition.
grub rescue>

Now I cannot access my Windows partition. I know absolutely nothing about Linux, Ubuntu, or Grub. I know nothing about bootloaders, boot CDs, or anything else involving booting other than hitting a power button. Consider me to be completely computer illiterate. I've spent the last 3 hours scrounging the internet, trying to find a solution to this problem, and have found nothing of use.

I've already looked through these forums, and none of the solutions I've seen were remotely helpful, so please don't just tell me to look at the other threads. I've tried. I do not have any install discs, any blank discs, or any usable burners than can create discs for me, nor will I ever, so please do not suggest anything relating to that as a solution to this problem.

I just want to be able to use my computer without having to do a clean install on it again for no reason. Please help. Specs below if it matters:

Dell Studio 1458
Win7 Ultimate x64
Core i5-450M
512MB Radeon 540v
2x2GB DDR3-1066
320GB 7200RPM SATA 3Gb/s

---

### Post by Kirk Schnable on 2012-12-09
Your boot loader was messed up one way or another.  Since you do not want to go back to a dual boot environment, you will no longer be needing GRUB.  I suggest repairing your Windows 7 boot loader, which you can easily do with your original Windows 7 installation DVD and these simple instructions:
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by ctg867 on 2012-12-09
> **Kirk Schnable said:**
> I suggest repairing your Windows 7 boot loader, which you can easily do with your original Windows 7 installation DVD and these simple instructions:

Not to be rude, since I greatly appreciate your help and your quick response, but:

> **ctg867 said:**
> I do not have any install discs, any blank  discs, or any usable burners than can create discs for me, nor will I  ever, so please do not suggest anything relating to that as a solution  to this problem.

My computer never came with Windows install discs. Most computers don't these days. You have to pay extra for them (ie: HP) or you have to call and order them (ie: Dell). This isn't a viable option for me. Would you happen to have any other solution that might work for me? Thanks again.

---

### Post by Kirk Schnable on 2012-12-09
> **ctg867 said:**
> Not to be rude, since I greatly appreciate your help and your quick response, but:



My computer never came with Windows install discs. Most computers don't these days. You have to pay extra for them (ie: HP) or you have to call and order them (ie: Dell). This isn't a viable option for me. Would you happen to have any other solution that might work for me? Thanks again.

Sorry, I read up to a point on your thread, and I figured I had an answer.  I try to get to as many threads as I can when I have time to help out here, so I don't always read cover to cover, especially if I know a simple fix up front.

If you have another computer (or a friend) with a working Windows 7 installation, you can make a USB flash drive into a bootable recovery media which will get the job done.

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by Kirk Schnable on 2012-12-09
Your other option, might be to reinstall GRUB.  The GRUB boot loader might still be able to trigger what's left of your Windows 7 boot loader, since it sounds like it worked before, and your Windows 7 partition hasn't been altered.

It should be theoretically possble to use Boot Repair and reinstall GRUB, even though you have no plans of using it for Linux anymore.  GRUB is still a perfectly legitimate boot loader to use in front of Windows 7, as long as Windows 7 has bootable information left in its partition.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

