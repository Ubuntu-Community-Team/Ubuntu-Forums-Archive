---
title: "The agony of using a usb pen drive"
date: 2005-06-10
forum: General Help
---

### Post by tmckellar on 2005-06-10
Greetings,

I started using Ubuntu about two weeks ago and have been rather impressed thus far. Had some trouble with my sound at the start (the sound support was much worse in FC3) but got it under control. The problem I'm having now is with the latest updates. When I initially installed Ubuntu my usb pen drive functioned properly in Ubuntu. Now that I have updated my version of Ubuntu I can't get it to mount. I read in a thread about a similar problem to go into /etc/fstab and change some stuff for the pen drive. That didn't work. Only gave me a different error. My initial thought was that I janked something up in the pen drive using it on Windows trying to transfer some emails from Thunderbird in Windows to Thunderbird in Ubuntu. I tried the drive on the Live CD and it opened it up no problem so my only conclusion it is in the updates I got. The error it gives me tells me the drive is in an unusable format as none was specified. If anybody else is having this problem and has found a solution I would appreciate some info on how to fix it. I've thought about downgrading gnome-volume-manager but am not sure how to do so, so if anyone knows how to do that I will try that. Thanks

Tyler

---

### Post by Jesus Franco on 2005-06-10
Hey. It would really help if you post your fstab on the forum.
Then maybe one can help you.  :-P

---

### Post by tmckellar on 2005-06-10
I'll check it out when I get home. I'm at work at the moment.

---

### Post by tmckellar on 2005-06-11
Here's what fstab says

    GNU nano 1.2.4                                                        File: /etc/fstab# 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

The bottom line is for the usb pen drive

---

### Post by Alexander Kirillov on 2005-06-11
[QUOTE=tmckellar]Here's what fstab says

    GNU nano 1.2.4                                                        File: /etc/fstab# 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

The bottom line is for the usb pen drive[/QUOTE]
 Should be /dev/sda1, not /dev/sda

---

### Post by tmckellar on 2005-06-11
Good Lord. That was the easiest fix I've ever seen. Thanks.

---

### Post by kvidell on 2005-06-11
[QUOTE=tmckellar]Good Lord. That was the easiest fix I've ever seen. Thanks.[/QUOTE]
 It's always the smallest typos that muck things up the worst :)

---

### Post by tmckellar on 2005-06-12
Now I've stumbled upon a new problem. /dev/hdc is my DVD-Writer. /dev/hdd is my stock CD-burner. /dev/scd0 is my usb CD-Writer. My DVD-Writer will read dvd's but none of my drives will read blank cd's or audio cd's. Is there anything in /etc/fstab I can change to get them to work. I really appreciate the help thus far. Thanks.

---

### Post by Alexander Kirillov on 2005-06-13
[QUOTE=tmckellar]Now I've stumbled upon a new problem. /dev/hdc is my DVD-Writer. /dev/hdd is my stock CD-burner. /dev/scd0 is my usb CD-Writer. My DVD-Writer will read dvd's but none of my drives will read blank cd's or audio cd's. Is there anything in /etc/fstab I can change to get them to work. I really appreciate the help thus far. Thanks.[/QUOTE]
 Nope - it is not an fstab problem. Ask in hardware subforum, and give make and model of the drives...

---

