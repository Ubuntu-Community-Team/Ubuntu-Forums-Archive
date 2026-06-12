---
title: "uninstall or remove Ubuntu 8.04"
date: 2008-05-10
forum: General Help
---

### Post by irv on 2008-05-10
I just upgraded to Ubuntu 8.04 on my Dell Inspiron 1521 laptop and there are so many Issues I am going back to my old laptop. My questing, is there a way to remove or uninstall Ubuntu and recover the drive space so I can use it with Vista? Seeing I have two laptops I am going to run Ubuntu on one and Vista on the other.
I tried gparted, but the CD won't even boot on the Inspiron 1521. Dell really changed their hardware.
Thanks for your help a head of time.
Irv

---

### Post by ghost_ryder35 on 2008-05-10
boot into vista and delete the ubuntu partiton then boot into the recovery option off the vista cd and run the commands fixmbr and fixboot.  if you only have ubuntu installed just install vista and delete all partitons then make a new partion the size of the entire disk and format it

---

### Post by Herman on 2008-05-10
I agree with the previous poster but I have read that the FIXBOOT and FIXMBR commands are slightly different for Vista, **See lswest's and bodhi.zazen's thread**, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB]("http://ubuntuforums.org/showthread.php?t=740221").

Actually, neither Ubuntu nor GRUB ever touch your Windows boot sector, so you only need the Vista equivalent of FIXMBR.

---

