---
title: "Need help with storage, LiveCD, etc...."
date: 2008-06-02
forum: General Help
---

### Post by Tristicus on 2008-06-02
Well, I downloaded Hardy after wanting to get back into Linux this summer, and I burned it to a disc at full speed, checked integrity, everything was cool. Well, when I put the disc in to boot it, I selected the menu, and it went through the sliding bar, then came up with a black screen and blinking cursor, and started going through checks/commands...it would repeat them, and go through the same thing, saying the same "errors" and such. There are some pictures of it below. I really want to know what is wrong.
[[IMG]http://img117.imageshack.us/img117/4986/hpim0551bk8.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img136.imageshack.us/img136/9174/hpim0548em6.jpg[/IMG]](http://imageshack.us)

---

### Post by Tristicus on 2008-06-02
Any help....?

---

### Post by Tristicus on 2008-06-10
Umm...some help? Still getting the same thing with a trackball PS/2 mouse.

---

### Post by bluepowder7 on 2008-06-10
no idea on the cd reading errors

you can combine a bunch of drives using LVM into one larger drive.  for example, on my file server, i have a 120G IDE, 250G IDE, and 750G SATA all combined under LVM into one large 1.1TB drive.  no RAID, just mass storage.  if you search for "ubuntu server guide LVM" you should be able to find the commands to set it up.  not sure if it would be readable by windows, though, but linux will take it just fine.

note that using ext2 or ext3 file systems, you lose some capacity.  using jfs is much better, and xfs is better still.  i stupidly set mine up using ext2, but when i get another drive i'm gonna migrate it all to xfs (gonna take a lot of manual work, though, but the space regained will be worth it)

---

### Post by Tristicus on 2008-06-10
Thanks for that. i am just gonna raid them though.

NEED HELP WITH LIVECD! I want to get it installed TONIGHT!

---

### Post by Tristicus on 2008-06-10
Also, I tried it again, and it started giving me stuff about ATA errors and resarting the device and crap.

---

### Post by Tristicus on 2008-06-10
....

---

### Post by issih on 2008-06-10
this thread might help you out...

[http://ubuntuforums.org/showthread.php?t=651872](http://ubuntuforums.org/showthread.php?t=651872)

Looks like the most success came from fiddling with the sata hardware wiring set up one way or another

good luck

---

