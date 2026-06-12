---
title: "Error Mounting CD"
date: 2017-04-02
forum: General Help
---

### Post by ThePowerpuffGirls on 2017-04-02
When I put it in, I get the following:

'Unable to mount Aug 30 2004

Error mounting /dev/sro at /media/chloe/Aug 30 2004: Command-line 'mount -t "iso9660" -o
"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500"
"/dev/sr0" "/media/chloe/Aug 30 2004'" exited with non-zero exit status 32: mount: /dev/sr0 is
write-protected, mounting read-only
mount: /dev/sr0: can't read superblock'

I've tried it in another computer and other CD work fine.

It is SATA drive and other CDs have worked, its just this one particular. I've also tried it in another computer and the same thing, same error.

---

### Post by mc4man on 2017-04-02
Maybe the cd is damaged beyond use. Outside possibility is that it was burned in Win Xp as a live session disc. If possible  try it in a windows machine.

---

### Post by ThePowerpuffGirls on 2017-04-02
OK, will try it under Windows and let you know. Thank you.

---

### Post by ThePowerpuffGirls on 2017-04-03
It worked under Vista, however strangely it shows only 6-7 MB used and nothing on the CD.

---

### Post by izznogooood on 2017-04-03
sudo apt install exfat-utils

---

### Post by ThePowerpuffGirls on 2017-04-04
I will try it today and let you know, thank you. :)

---

### Post by ThePowerpuffGirls on 2017-04-05
I'm sorry for the delay; I;ve been very busy.

I've downloaded the exfat, is there something I should do before mounting the CD?

---

### Post by izznogooood on 2017-04-06
No, just install the exfat-utils package. This solves my problems with memory cards so it's worth a shot.

---

