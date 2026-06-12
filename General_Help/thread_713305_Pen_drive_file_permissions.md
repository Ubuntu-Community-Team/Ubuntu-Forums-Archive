---
title: "Pen drive file permissions"
date: 2008-03-02
forum: General Help
---

### Post by Mateo on 2008-03-02
I'm having trouble with permissions on my USB drive.  I put it into my desktop computer and make myself the owner of the files.  Like this:

```
sudo chown -R matthew /media/mypendrive
```

But then when I take it out of the computer and put it into my laptop I have the same problem!  I have to chown everything to myself, then when I go back to the desktop I'm locked out.  How can I have it so that on BOTH computers my user can access the files?  Read-write everything.  By the way, my desktop is using ubuntu and my laptop is using fedora.  Thanks.

---

### Post by Crooksey on 2008-03-02
You shouldnt have to chown a pendrive... what filesystem is on it?

---

### Post by Mateo on 2008-03-02
ext3

---

### Post by Crooksey on 2008-03-02
Try using vfat, if you dont mind reformatting.

ext3 being a *NIX filesystem has permission issues, vfat does not.

Well, I have sevral vfat pen drives, and never had to chown a it.

---

### Post by Mateo on 2008-03-02
Anyone else have any ideas?

---

### Post by Mateo on 2008-03-03
bump.

---

### Post by christian130 on 2008-03-03
please what u can do now
is stop AUTO LAUNCHING THE PEN DRIVE
what u have to do is
**umask=000**
i had the same problem when sudenly my NTFS partitions could not read for everyone
please check:



user@machine:/user/home$sudo mount -o rw,umask=000 -t ext3 /dev/sda0 <destination route>

u can set it up in services etc/init.d/ launched at boot system or u can try some of it


hope it could help for something, more information here:
[http://milyunpayasadas.blogspot.com/]("http://milyunpayasadas.blogspot.com/")

---

### Post by Mateo on 2008-03-04
thanks, any one else have ideas?

---

### Post by Mateo on 2008-03-05
Bump.

---

### Post by BRAXS69 on 2008-03-05
yeah i sometimes have that same problem i usaly fix it by adding the "-hR" option to chown
sudo chown username -hR /media/pendrive ~but that will only make owner of the drive..
you might want to try having the same user name on all machines so that the permissions will work the same on all devices...

---

