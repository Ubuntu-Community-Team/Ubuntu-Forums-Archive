---
title: "Trust webcam 14382 and skype"
date: 2012-11-03
forum: General Help
---

### Post by Hesediel on 2012-11-03
I am running kubuntu 12.04
The webcam works with cheese and on test on phonon.

It doesn't work on skype. 

The code LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype doesn't work the terminal gives ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

lsusb recognize it

Bus 002 Device 005: ID 093a:2468 Pixart Imaging, Inc. SoC PC-Camera

Is there a way to make it work with skype as with cheese?

---

### Post by Zorael on 2012-11-09
Huh, I thought the point of v4l1compat was being able to preload it.

Does the file exist to begin with?

Also, are you running a 64-bit installation?

---

### Post by gordintoronto on 2012-11-09
I think the file has moved and been renamed, so you need to modify the command. Try the command: locate libv4l

Perhaps it is here:
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

---

### Post by BertN45 on 2012-11-09
+1 for me it was as follows too:
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype

---

