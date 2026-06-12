---
title: "deleted partition unable to startup"
date: 2013-03-23
forum: General Help
---

### Post by three4thsforsaken on 2013-03-23
Hello everyone,

This is my first post!  

Hi, so I deleted my ubuntu partition today though my Windows 7 disk manager.  I had to restart my computer shortly afterwords.  Now my BIOs can no longer find my windows partition and send me to a grub restore command line.  I would like for my computer to find my windows partition but I don't really understand how.  

This is what I know:

1.)Ubuntu 9.10 and Windows 7 are on the same hard drive.

2.) In the past Ubuntu 9.10 was my default OS when turning on the computer, I would need to move through the OS list to boot off of Windows 7

3.) The partition that used to contain the ubuntu partition is now an empty partition

I think it has something to do with my grub information being correlated to my ubuntu partition and deleting it lost the grub information.  But I am not confortable with those statements.  How should I go about fixing this problem?  And of the possible solutions do any involve not reinstalling Ubuntu just to use it's command line to update grub?

Thanks for your time.

Cheers,
3/4ths

---

### Post by fantab on 2013-03-24
When you installed Ubuntu its Boot Loader, GRUB had overwritten Windows MBR (Boot Loader) files. Grub was loading your windows. When you deleted Ubuntu partition you deleted the files required for Grub to boot Windows.

You will have to either re-install Ubuntu or [Fix Windows]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html").

---

### Post by mikewhatever on 2013-03-24
> **fantab said:**
> When you installed Ubuntu its Boot Loader, GRUB had overwritten Windows MBR (Boot Loader) files. Grub was loading your windows. When you deleted Ubuntu partition you deleted the files required for Grub to boot Windows.

You will have to either re-install Ubuntu or [Fix Windows]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html").

Good advice, however, strictly speaking, there is no such thing as "Windows MBR", and GRUB didn't load Windows, but rather passed the process on to the Windows boot loader, which, of cause, hasn't been overwritten.

---

### Post by fantab on 2013-03-24
> **mikewhatever said:**
> Good advice, however, strictly speaking, there is no such thing as "Windows MBR", and GRUB didn't load Windows, but rather passed the process on to the Windows boot loader, which, of cause, hasn't been overwritten.

Thanks. This is the second time I have been corrected in this matter. Could be so kind to please post some links so I can understand this more clearly. (I don't mean to hijack OP's thread) you can PM me. Thanks again.

---

### Post by Mark Phelps on 2013-03-24
The Windows boot process on a PC is as follows:  MBR --> PBR --> Windows boot loader

Essentially, the MBR points to the partition that contains the Windows boot loader.

When you install GRUB, it points to the partition that contains the Linux boot loader.

Thus, when you remove Ubuntu, the MBR still points to the Ubuntu partition -- which is now gone.  What has to be done to fix this is to update the MBR to point to the proper Windows partition.

---

### Post by mikewhatever on 2013-03-24
Here is a nice MBR article [http://members.iinet.net.au/~herman546/p6.html#What_is_the_MBR_or_Boot_Sector](http://members.iinet.net.au/~herman546/p6.html#What_is_the_MBR_or_Boot_Sector)

---

### Post by fantab on 2013-03-25
Thanks Mark Phelps and mikewhatver. That clears things for me.

---

### Post by three4thsforsaken on 2013-03-26
I followed Fantab's advice and after looking for my old window's 7 disk, it's all fixed!  Thanks Fantab, Mark Phelps and mikewhatever for all the great info and advice!

---

