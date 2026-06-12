---
title: "XDMCP login from cygwin now fails"
date: 2007-03-29
forum: General Help
---

### Post by flyrc51 on 2007-03-29
I was running 6.10 Gnome and it worked out of the box, in an hour or so ssh, samba and logging in from a PC via "C:\cygwin\usr\X11R6\bin\XWin.exe   -query 192.168.1.103" just worked.

It was so easy! so after a week or so I decided to try KDE as GNOME felt a little restrictive, I followed the how tos on installing this on top of GNOME and XDMCP from cygwin stopped working.

I assumed I had screwed up and deiced to install it fresh, and downloaded the 7.10 kde ISO CD,  after some false starts it installed, and everything appears to work perfectly.

However I still cannot login remotely, I have tried every variation of every help topic I can find, the last one I followed was [http://klomdark.servebeer.com:8081/MessageBase2/ReadMessage.aspx?MsgNum=1967]("http://klomdark.servebeer.com:8081/MessageBase2/ReadMessage.aspx?MsgNum=1967")

But now I get the following hard error, before this it was just a gray checkered screen from cygwin.

I am completely out of ideas other than deleting everything again and sticking with the (lesser in my opinion) option of GNOME.

Is there any thing I can do to debug this ?


```
_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
(II) XF86Config is not supported
(II) See [http://x.cygwin.com/docs/faq/cygwin-x-faq.html](http://x.cygwin.com/docs/faq/cygwin-x-faq.html) for more information
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shared memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409)
(--) Using preset keyboard for "English (USA)" (409), type "4"
(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap
(--) 5 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!

Fatal server error:
XDMCP fatal error: Session failed Session 325472001 failed for display 192.168.1.101:0: cannot open display

winDeinitMultiWindowWM - Noting shutdown in progress
```

---

