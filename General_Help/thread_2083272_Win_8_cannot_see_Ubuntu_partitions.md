---
title: "Win 8 cannot see Ubuntu partitions"
date: 2012-11-12
forum: General Help
---

### Post by Starmartyr on 2012-11-12
I have dual booted Windows 8 and Ubuntu 12 on my computer.  Under Win 8, I cannot see my Linux partitions.  Any easy way to view these partitions?

---

### Post by gerowen on 2012-11-12
Windows historically hates anything that isn't Windows.  If you install Windows after Ubuntu on a dual boot system, it will not recognize Ubuntu and add it to your boot menu, that's why it's always a good idea to install Linux last so it will detect the other systems and add them to your Grub bootloader.

Anyway, to answer your question, there is a piece of software called EXT2Fsd that I've used before, but the last Windows OS I used extensively was Vista, so I'm not sure if it will work with Windows 8, and I've heard of people occasionally borking up their Linux partitions by mounting them in Windows with 3rd party software like this.  Personally I've never had an issue, but it has been a long time since I've used Windows and had to do this, so it's something to be aware of.

You can check it out at: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by Starmartyr on 2012-11-12
I did install ubuntu after Win 8.  I initially had a broken grub, then found the grub repair tool, and it fixed it.  Now it's great.

I tried EXT2Fsd just now, but their last update/version was mid, so that didn't work.  No Win 8 compatibility.  Thanks for the try.

Still searching...

---

### Post by oldfred on 2012-11-12
We normally suggest that you do not directly write into another systems' system partition.  Or even though Linux's NTFS driver shows the Windows system partition do not write into it, but set it read only if you do want to copy data from it.

Then create a shared NTFS data partition that both systems can read & write.
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

Windows standard shutdown is a hybrid hibernation, so be careful.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

