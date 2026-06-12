---
title: "Packard Bell MP3 player: insufficient space"
date: 2005-09-14
forum: General Help
---

### Post by ArthursArts on 2005-09-14
I'm having a problem with this USB Packard Bell MP3 player. I connect it, and it is detected, mounted, and there is a window opened with its contents. Then, when trying to drag and drop a new song to it, it doesn't work.
It tells me that there is insufficient space. Which can't be true because only 190 of 512 MB is in use. Nautilus says that there is only 1.6 MB free. When I remove a few songs (3 MB+), it still reports only 1.6 MB free, which ofcourse is not true.

I looked in mtab, and usbfs was mounted. When I unplugged the MP3 player, it was still mounted.

What can I do?

Thanks in advance.

---

### Post by mlomker on 2005-09-14
That's odd.  Plug it in and post the output of the following command.

From a terminal prompt:

```

sudo fdisk -l

```

---

### Post by ArthursArts on 2005-09-15
Indeed, since it worked on the installation before this one. 

Schijf /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1   *           1         125     1004031   83  Linux
/dev/hdb2             126        1371    10008495   83  Linux
/dev/hdb3            1372        1559     1510110   82  Linux swap / Solaris
/dev/hdb4            1560        4865    26555445    5  Uitgebreid
/dev/hdb5            1560        2182     5004216   83  Linux
/dev/hdb6            2183        4865    21551166   83  Linux

Schijf /dev/sda: 521 MB, 521797632 bytes
211 heads, 46 sectors/track, 105 cylinders
Units = cylinders of 9706 * 512 = 4969472 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/sda1   *           1         105      509542    b  W95 FAT32


Note, I've translated some words from Dutch to English (heads, sectors etc), so they might not be completely accurate. The devices are though.

I also tried it on my Gentoo box, there it too reported only having 1.6 MB free.

---

### Post by mlomker on 2005-09-16
It is showing the proper size in fdisk.  Have you tried to reformat it?  Perhaps there are some hidden files on the partition that Windows can see but linux cannot.

p.s.  I spent a week in Amsterdam last March and it was wonderful.  :-)

---

### Post by pmj on 2005-09-16
It's possible that the files you deleted aren't gone at all, only moved to the trash. The trash here being a hidden folder on the mp3 player. This happened to me the first time I tried my mp3 player.

---

### Post by ArthursArts on 2005-09-16
Thanks for the replies. Indeed the removed files were moved ,Trash, and after having emptied the trash the 1.6 MB was enlarged to 4 (yay!). 
Then I connected it to an old Win2000 computer I remembered having and there it displayed the correct space left, 303 MB. 
I noticed then that that computer used a USB 1.1 port and that Linux used a USB2.0 (PCI extension) port. Luckily the Linux box also had a USB1.1 port and trying that one... it worked?!
For some reason it gives the wrong value on USB2.0 and the right on USB1.1?

Anyway, thanks for the help. It works now, strange though that it doesn't work correctly on USB2.0.

---

### Post by Zeno Cosini on 2006-07-12
Could you please let me know which mp3 player from Packard Bell you are using? I have just received a Packard Bell AudioTwin as a present (it's still factory sealed), and I would like to be sure that it works on my machine (Ubuntu and USB 2.0) before opening the box.

Thanks.

---

