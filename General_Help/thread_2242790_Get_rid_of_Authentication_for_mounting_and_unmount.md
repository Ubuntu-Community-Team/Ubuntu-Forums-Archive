---
title: "Get rid of Authentication for mounting and unmounting USB Drives"
date: 2014-09-04
forum: General Help
---

### Post by Floyd_Wallace on 2014-09-04
Help! I'm using Xubuntu 14.04 Trusty Tahr, and everything was working fine until I added the LSB packages (in order to install the Epson Wireless Printer drivers for my Epson XP-410 printer ... which is excellent by the way).

Now I get an authentication message every time I want to mount (i.e. I insert/hot plug a USB drive) or unmount (eject it). Obviously I need these packages, I tried removing them and they would also remove my Epson Printer packages.

I'd like to simply authenticate myself once and for all, but searching through man pages I get nothing.

Is there some trick with PAM to get rid of the authentication message? I need my printer but I also HATE that authentication nag. Yes I automounted my USB drive. And ejected it! Don't nag me on that stuff. Heck its a Laptop and often, speed counts a lot when I need to shut down.

I assume that lsb-security package is now giving me the nag, I'd like to dump the nag is all.

Thanks.

---

### Post by deadflowr on 2014-09-04
If you run the command
```
id
```
is one of your groups plugdev?
If not, you might need to add it, i think...
Here's a good page on all that
[http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu](http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu)

---

