---
title: "iPhone and Amarok lockfile issue"
date: 2008-01-06
forum: General Help
---

### Post by jokr004 on 2008-01-06
Ok, I'm trying to mount my iphone with sshfs to work with amarok.  In amarok, I'm using the whole ipod-convinience thing as a mount command but when it tries to mount it I get 

Media Device: failed to create lockfile on iPod mounted at /media/ipod: No such file or directory

amarok does mount the device at /media/ipod but fails to recognize this.

I've read somewhere that this is possibly caused by journaling being enabled on my iphone but it only explained how to disable journaling in a mac, which I don't have.  Does anyone know if this sounds like the problem, and if so, does anyone know how I could disable journaling in linux or windows?

---

### Post by ntetreau on 2008-01-06
jokr004:  It might just me a misconfiguration or even a bug in ipod-convenience.  I'll try to think of a solution but in the meantime, do a quick "search" in this thread for your problem:
[http://ubuntuforums.org/showthread.php?t=588246&highlight=iphone](http://ubuntuforums.org/showthread.php?t=588246&highlight=iphone)

and make sure you follow exactly all the steps in this wiki:  
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Nic

---

### Post by darkkith on 2008-01-06
I am having this same problem with amarok - it does not appear to be a problem with ipod-convenience since i can sync via gtkpod.

---

### Post by darkkith on 2008-01-06
alright after a lot of mucking around and haphazardly trying stuff i figured out the problem is i did not symlink iTunes to itself ... 

that doesn't make sense.. i know.

1. ssh to your ipod touch.
2. cd /var/root/Media
3. ls -lh iTunes

this SHOULD be iTunes -> .
if it is not, make it so:

mv iTunes iTunes.bak
ln -s iTunes .

wala...

---

