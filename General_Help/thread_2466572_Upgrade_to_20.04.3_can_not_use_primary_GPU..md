---
title: "Upgrade to 20.04.3 can not use primary GPU."
date: 2021-08-31
forum: General Help
---

### Post by wANGExM on 2021-08-31
I just upgraded from 18.04.5 to 20.04.3 (clean install not do-release-upgrade). Using nVidia 470.57.02 The system can no longer use my primary GPU. It defaults to the "crappy" secondary GPU. If I enable my screens - add another XScreen for the screens on the main GPU xfwm (and most things) crash and glitch out.
```
(xfwm4:3126): Gdk-ERROR **: 22:09:25.726: The program 'xfwm4' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadPixmap'.
  (Details: serial 0 error_code 161 request_code 150 (GLX) minor_code 16)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)
```
In dmesg I get
```
[ 714.705496] xfce4-session[4220]: segfault at 0 ip 00007fe6373d5b7e sp 00007ffd4ef0d048 error 4 in libc-2.31.so[7fe637274000+178000]
[ 714.705510] Code: 0f 84 fd fe ff ff e9 01 80 f3 ff 90 f3 0f 1e fa 89 f8 31 d2 c5 c5 ef ff 09 f0 25 ff 0f 00 00 3d 80 0f 00 00 0f 8f 52 03 00 00 <c5> fe 6f 0f c5 f5 74 06 c5 fd da c1 c5 fd 74 c7 c5 fd d7 c8 85 c9
```
I had this all working fine on 18.04. If I enable Xinerama I can use both GPU and all screens but it causes tons of other problems.
During the install I noticed the Nouveau drivers saw both GPU's and all screens (it never had previously) but if I enabled the screens on the primary GPU the system basically dies a slow laggy death.

I'd also like to know why 20.04 enumerates the PCIe slots backwards...bottom up if you will.
Checked out a live session on 21.04 as well. Problem persists. It enables the PCIe1 GPU and if I enable anything on the primary GPU the system goes kerput.

---

### Post by mastablasta on 2021-08-31
purge nvidia and reinstall.

---

### Post by wANGExM on 2021-08-31
Not sure why I'd do that when it's a clean install, tested on live and bare metal with Nouveau and proprietary...also tested on 21.04 - same. ***You do make me realize an issue with my wording. Upgrade! I didn't use do-release-upgrade, I did a clean install it's just an "upgrade" from the prior install. I'll edit that!

---

