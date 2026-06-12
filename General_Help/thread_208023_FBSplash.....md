---
title: "FBSplash....?"
date: 2006-07-02
forum: General Help
---

### Post by noob_Lance on 2006-07-02
Hey,

Ive seen talk of this program fbsplash... i was wondering what it is and what does it do? 

Any info is appreciated.

Regards
~Lance

---

### Post by mbeierl on 2006-07-04
As far as I know, FBSplash is an alternative to the more widely compatible USplash that Debian/Ubuntu has chosen for boot time messages.  It uses the full capabilities of the framebuffer (FB) which, if supported by your card, can give you a beautiful 1280x1024x32bit colour graphical boot.

It requires a kernel recompilation though.  It is not available as a prebuilt kernel through apt sources.

See [http://www.ubuntuforums.org/showthread.php?t=178439](http://www.ubuntuforums.org/showthread.php?t=178439) for more info on how to roll your own if you'd like to try it.  I haven't taken the leap yet, but I think I might soon - it's just so tempting!

---

