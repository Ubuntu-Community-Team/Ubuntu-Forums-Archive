---
title: "[SOLVED] ATI Driver Upgrade - Problem(s)"
date: 2008-06-09
forum: General Help
---

### Post by MattP220 on 2008-06-09
I recently tried to install the Linux client for EVE Online.

I was using the restricted driver manager to handle my card, an ATI mobility radeon X600. I also run Compiz with Xgl. 

On installing the game, OpenGL was found to be lacking. Meaning, it didn't work.

I went to the ATI site and downloaded the latest driver, 8.5 and attempted to install it. 

That's really where the problems began. 

I found this thread [http://ubuntuforums.org/showthread.php?t=817542](http://ubuntuforums.org/showthread.php?t=817542) that seemed to detail a similar process, but when I attempted the steps outlined, this is what I get:

sudo dpkg --purge xorg-driver-fglrx
(Reading database ... 137126 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
  found `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx

The same error comes out when I try un-installing via synaptic. So at this point I seem to be stuck bad spot -- I can't really go backwards or forwards until I get that snag undone. 

As of right now, openGL is still off and so is my rendering -- Compiz isn't working and frame rate is atrocious (not to mention killing CPU cycles...)

The goal for the mean time is to 1) get rendering back so I can have my pretty desktop back and actually read web pages and 2) get openGL functioning, which was the original goal.

Thanks for any input.

---

### Post by MattP220 on 2008-06-09
OK I managed to remove the xorg-driver-fglrx that was causing the hangups. 

I removed it, then reinstalled the restricted driver from the repositories, and it was working fine (except for lack of Compiz). 

Unfortunately after I rebooted, I can't get past Ubuntu's splash screen. 

It goes through the motions as it's supposed to, but after the splash screen, it goes black a little longer than it should, then dumps me back to an output screen with a blinking cursor. That's as far as it will go.

Any ideas??

---

