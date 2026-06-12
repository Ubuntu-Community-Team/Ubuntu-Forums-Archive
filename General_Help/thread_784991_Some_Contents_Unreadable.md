---
title: "Some Contents Unreadable"
date: 2008-05-07
forum: General Help
---

### Post by angryrabbit on 2008-05-07
Hey guys,

I guess I should tell you some background info first... so I had a problem when my NTFS file system on my boot drive changed to RAW, and XP gave me a BSOD, so I got testdisk and an external enclosure and transferred all my stuff to another computer, then I installed Ubuntu, and then transferred all my files back.

Now I get the error "Some contents unreadable" when I click properties on the File System, It shows that 17gigs are being used, and 300mb free. But its a 40 gig hdd, and it really restricts what I can do. And I have no clue.. Any help is welcome, and Thanks in advance.

---

### Post by angryrabbit on 2008-05-11
The problem still isn't solved, I don't think its a partition problem, so the only option I can think of is to reformat and install Ubuntu again, any suggestion?

---

### Post by Sef on 2008-05-12
Applications > Accessories > Terminal

then this code:

```
sudo fdisk -l
``` Small L

then paste the results here.

---

### Post by angryrabbit on 2008-05-13
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4774    38347123+  83  Linux
/dev/sda2            4775        4864      722925    5  Extended
/dev/sda5            4775        4864      722893+  82  Linux swap / Solaris

---

### Post by angryrabbit on 2008-05-20
So, i popped in the cd I got with the harddrive, and formated the drive, and installed ubuntu again, to no awail, I'm guessing its the harddrive so I'll install  XP again to make sure... Suggestions still welcome

---

