---
title: "USB Pen Drive w/ Live CD"
date: 2004-10-30
forum: General Help
---

### Post by Luke on 2004-10-30
New to Linux, new to Ubuntu...

i've been playing around with the live cd a little bit and I really like it. i'd like to use it to retrieve some files from a friend's computer on which windows is screwed up. Unfortunately, she only has 1 cd drive so i can't burn the files to cd. i was hoping to be able to use a usb pen drive but i'm not sure how to mount the drive when running with the live cd.

thanks

---

### Post by TekMate on 2004-10-30
If it doesn't auto mount try this open a terminal and type sudo su put in your password now cd /mnt and type mkdir pendrive now mount -t auto /dev/sda1 /mnt/pendrive this should work if you have any questions post back.

---

### Post by Luke on 2004-11-02
thanks for the quick response. i tried that on my machine and it didn't work. the problem on the machine i actually wanted to use it for was much more severe than i'd thought. it has a defective motherboard so i'm waiting for dell to send a new one. anyhow, i'll play around with it some more when i have some time and give the exact message i get when i try what you posted.

incidentally, knoppix detects both of my usb pen drives automatically when i plug them in.

thanks

---

### Post by jdong on 2004-11-02
Ubuntu should be better than Knoppix at that... weird. when I plug my Sandisk Cruzer mini into my Ubuntu system, Nautilus even pops up, browsing all the files!

---

### Post by jwenting on 2004-11-04
I have the same problem with an installation (so not live CD) with one of my pen drives.
Another one works just fine.

My guess is that the responsible driver doesn't like some pen drive hardware (there's several flavours out there from what I've been able to determine).
The drive will show up in the device manager but the filesystem cannot be mounted.

The drive that doesn't work I can't tell the make and model (it was given to me as a marketing gimmick and has only the name of the company I work on it).
The one that does work is a Sweex 256MB drive.
[http://www.sweex.com/product.asp?pid=102](http://www.sweex.com/product.asp?pid=102)

I haven't tried any other models.

Update: just added a 1GB Sandisk USB2 stick which works just fine.

---

