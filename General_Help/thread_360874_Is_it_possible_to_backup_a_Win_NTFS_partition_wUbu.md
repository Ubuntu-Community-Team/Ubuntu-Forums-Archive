---
title: "Is it possible to backup a Win NTFS partition w/Ubuntu?"
date: 2007-02-13
forum: General Help
---

### Post by caffienda on 2007-02-13
I have a few XP Pro drives that I would like to backup without using Ghost.  I was wondering if I put a HD's with XP on it into my Ubuntu box, could I mount that drive and back it up somehow?

Could I use partimage, or even tar it with "tar cvpfz XPBal.tgz "?

If this is possible, what is the best way to restore the image after creating it?

---

### Post by drpaul on 2007-02-13
I have done it with partimage. I boot from a CD and send the image to a usb drive. I have the usb drive formatted in fat32 so Windows can see it too. If you are willing to risk the Linux ntfs writing capability, you could use that or even ext3 if you don't need Windows access. 

Yes, I know that there are drivers to allow that, but I hate dealing with new or experimental things when doing backups.

HTH

Paul

---

### Post by Imsati on 2007-02-13
Love this program

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It allows XP to read ext2/3 drives and move files from your XP disk to your Linux.

---

