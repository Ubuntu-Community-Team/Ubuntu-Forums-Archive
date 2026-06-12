---
title: "Ubuntu boot..."
date: 2007-03-10
forum: General Help
---

### Post by Somebody-Z on 2007-03-10
I recently received an old Compaq Presario 9660 as a gift. I Put a new 15 gig, unformatted hard drive in it and want to install Ubuntu Edgy Eft. However, for some reason I cannot edit the boot options or anything (I already contacted Compaq customer support, and they were no help) Since there is no operating system on the hard drive, it checks the floppy drive and,since there is no floppy disk, it fails to boot. I was wondering if there was any kind of boot disk that would allow me to boot Ubuntu off the CD.

---

### Post by Herman on 2007-03-10
Hello Somebody-Z,
The most popular nowadays is [Super Grub Disk]("http://supergrub.forjamari.linex.org/") which can also do a great number of other things for you as well. (Except wash your dishes) :)

Regards, Herman :)

---

### Post by Somebody-Z on 2007-03-11
Ok, I have the Super GRUB floppy disk, but I can't find how to make it boot the CDROM, Can anyone help?

---

### Post by Somebody-Z on 2007-03-11
Anybody?

---

### Post by Herman on 2007-03-11
Hello Somebody-Z,
I'm sorry, I thought you meant you needed a bootable CD that will boot your hard drive. 
Now I understand it's your CD drive that your are trying to boot.

Normally I would just change the boot order in the CMOS, (BIOS). Here's an example, but it's not the same BIOS as you have, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm").

I remember working on a nice old Compaque Pressario not long ago for a freind and I also found it hard at first to change the boot order in CMOS. After a while I realized that it required an unusual way of using the keyboard. Instead of using the up and down arrow key, if I remember correctly it was the left and right arrows instead that changed the boot device.
Try playing around with the keyboard while you are in the boot order settings in CMOS and see if you can find out which keys to use. Surely it must be able to be changed somehow.

Regards, Herman :)

---

