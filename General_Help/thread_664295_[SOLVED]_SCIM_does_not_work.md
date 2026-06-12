---
title: "[SOLVED] SCIM does not work"
date: 2008-01-11
forum: General Help
---

### Post by yc2 on 2008-01-11
Hello,

SCIM does not work

I just updated from Ubuntu 7.04 to 7.10. Basic system functions seem to be intact. However, I cannot use SCIM. Before upgrading the system I just pressed <ctr>/<space> to switch between input languages. When I now press this key combination (Gedit or Open Office), nothing happens. (I use Gnome.)

The language I want to input (Chinese) is installed and it can be read but not input. In the system tray I can see an icon looking like a keyboard. Through this icon I can reach "SCIM setup".

I wonder if SCIM is running at all? I try the following:

```
me@ubuntu:~$ scim -d
Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.
me@ubuntu:~$ 
```

Would be really grateful for help. :)  Thanx.

---

### Post by yc2 on 2008-01-11
It seems, using the method indicated on the following page will take care of the problem I had with SCIM:
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)
The problem in this thread can be regarded as solved. :)

---

