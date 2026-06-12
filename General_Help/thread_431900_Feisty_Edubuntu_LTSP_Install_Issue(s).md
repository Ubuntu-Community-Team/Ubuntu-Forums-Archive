---
title: "Feisty Edubuntu LTSP Install Issue(s)"
date: 2007-05-03
forum: General Help
---

### Post by smhickel on 2007-05-03
I upgraded to Feisty while on Ubuntu. Then wanted to get LTSP going. Loaded Edubuntu desktop, etc and ltsp from synaptics.

All going well (after 6 hours of working on it) except I get a pxe client to start loading edubuntu start up screen then stops and blinks off and on at a login screen. I saw an error having to do with mount and < 28 and saw a post somewhere that said to modify the nfs file with a timeout greater than 3 (was at 1). I set it to 10. I then did dpkg-reconfigure in a chroot of /opt/ltsp/i386. Now the mount <28 error is missing, but the screen still blinks off every 10 seconds and I can not get to a gui login.

Any thoughts?

Steve

---

### Post by smhickel on 2007-05-03
I see these errors on the screen (in between blanking out):

loading vmlinuz....
loading initrd.img.....
Ready.
Loading, please wait...

then eventually...

mount: I/O error
short read: 0 < 28

On the bottom of the screen it has a "login:" (but the screen blanks in and out every 8 or so seconds.

---

### Post by smhickel on 2007-05-03
Alas, I went to another machine and pxe boot it and it works fine. So there is something wrong with my other computer. Now to figure out what??

---

