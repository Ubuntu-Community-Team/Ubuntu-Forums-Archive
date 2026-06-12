---
title: "Automation of GUI application"
date: 2007-07-26
forum: General Help
---

### Post by ludovicc on 2007-07-26
Hello, 

I would like to automate some of my tasks on Ubuntu, like filling automatically the passwords for login on my bank with FireFox, creating a quick shortcut a la QuickSilver to enter a new task in Thunderbird/Lightning... 

In the Windoze world, there is a nice application called AutoHotKey (GPL!) that gives you complete control of the computer. Does anybody know of an equivalent in Ubuntu.

I've done some research, and all I've found was:
* DogTail
  [http://www.redhat.com/magazine/020jun06/features/dogtail/](http://www.redhat.com/magazine/020jun06/features/dogtail/)

* LDTP - GNU/Linux Desktop Testing Project 
   [http://ldtp.freedesktop.org/wiki/LDTP_Demo](http://ldtp.freedesktop.org/wiki/LDTP_Demo)

Those 2 programs are both some kind of GUI-driven unit testing frameworks. They probably work, but LDTP is not even in the Ubuntu repositories. Does anybody know of some more user-friendly automation software?

Thanks,
Ludovic

---

### Post by ludovicc on 2007-08-01
(Post to self)

Use a combination of XBindKeys ([http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)) and XMacro ([http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/))

Here is a nice tutorial:
[http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html](http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html)

It works, but it's still not as nice as AutoHotKeys: no support for menu navigation, no localisation of gui controls except by (X,Y) coordinates, not integrated...

---

