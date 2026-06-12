---
title: "iMac EFI Grub rescue"
date: 2014-10-03
forum: General Help
---

### Post by Tithos on 2014-10-03
I am on a 2012 iMac single booting into Ubuntu. 

I am get the grub rescue screen at boot and am having trouble fixing the problem.  

no matter what I set the prefix to I get an error.

I've tried

set prefix=(hd0,gpt2/boot/grub

set prefix=(hd0,gpt2)/boot/grub/x86_64-efi

Set prefix=(hd0,gpt2)/usr/lib/grub

Set prefix=(hd0,gpt2)/usr/lib/grub/x86_64-efi

No matter what i try, i get an error.

I try 

insmod linux 

It appends /i386-pc to the end of the prefix and throws an error

Surely i am not alone any help is great.

I have not been able to get live booting dvd to load at all and i do not have access to another pc to make USB

Thanks

---

### Post by oldfred on 2014-10-04
I do not know Mac, but the i386-pc is the BIOS version? 
I thought UEFI was better with a Mac?

 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

