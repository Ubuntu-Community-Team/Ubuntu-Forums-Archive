---
title: "usb pen drive wont work"
date: 2007-09-17
forum: General Help
---

### Post by fubar2511 on 2007-09-17
Hi guys i am new to this os but i actually like it problem is that after installing ubuntu server 64 bit i am having problems with usb drive. I have a 2 gig buffalo pen drive and when I plug it in it flashes like it should but but i cant find it to save my life.where has it gone,Do I need to mount it or type something into a terminal if so what do I type.Could someone please give simple instructions.

Looking forward to your reply's

fubar2511

---

### Post by pxwpxw on 2007-09-17
Try these, from a terminal
```

cat /proc/partitions 
df
mount
ls -l /media

```

---

### Post by fubar2511 on 2007-09-17
pxwpxw  many thanks m8 that worked a treat

---

