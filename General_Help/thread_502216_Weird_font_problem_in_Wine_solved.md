---
title: "Weird font problem in Wine solved"
date: 2007-07-16
forum: General Help
---

### Post by dwasifar on 2007-07-16
Today I opened up an app in Wine and instead of normal fonts, all the menubars, menus and tabs were filled with musical notes.  I opened up Winecfg and it was the same way.

Reinstalling Wine to a new directory resulted in a working Wine installation.  The fonts were still not right, though.  They were not musical notes any more, but they were some default system font; it looked like Courier.  Too big and wide, overspilling their space.

I did some poking around and comparisons, and discovered that my new installation had nothing in ~/.wine/drive_c/windows/fonts, whereas the original installation had Guitar_Pro_5.ttf in that folder.  This explained the musical notes.  I put a copy of FreeSans.ttf in ~/.wine/drive_c/windows/fonts, and Wine happily used that, although it was too small and caused spacing problems in the applications.  So I experimented a little more and got my best results with Tahoma.ttf brought over from a Windows box.  

Now Wine apps actually look better than they did before all this started.

---

### Post by AlexThomson_NZ on 2007-07-16
Thanks for the tip.  Out of interest- how do you find Guitar Pro 5 with wine?  I tried, and although it runs, it is VERY slow to render the screen, and cannot play anything (which is ok for now, as I am more interested in seeing the tab).  Any tips?

---

### Post by dwasifar on 2007-07-17
> **AlexThomson_NZ said:**
> Thanks for the tip.  Out of interest- how do you find Guitar Pro 5 with wine?  I tried, and although it runs, it is VERY slow to render the screen, and cannot play anything (which is ok for now, as I am more interested in seeing the tab).  Any tips?
Actually I can't even get it to run that far.  I installed it but I haven't actually been able to use it.  I admit I have not really put any effort into figuring it out, though.

---

