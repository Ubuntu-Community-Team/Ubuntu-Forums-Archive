---
title: "Problems with ATI mobiltiy x300 after Hardy Upgrade"
date: 2008-05-05
forum: General Help
---

### Post by pmgr33r on 2008-05-05
Hello,
So after upgrading to Hardy, everything has been running significantly slower. I have having all the same problems that I did in Gutsy when my graphics card would go out. (e.g. Choppy scrolling in firefox, choppy when opening new windows, choppy when dragging windows) I have tried to reconfigure x, making sure the ATI proprietary driver was turned on, and followed the ATI & Compiz known problems thread, none have worked. I tried metacity --replace and that has helped but everything is still running much slower than i know it should be. I was wondering if anyone else has encountered this problem and any known fixes

Thanks

---

### Post by finchair on 2008-05-07
> **pmgr33r said:**
> Hello,
So after upgrading to Hardy, everything has been running significantly slower. I have having all the same problems that I did in Gutsy when my graphics card would go out. (e.g. Choppy scrolling in firefox, choppy when opening new windows, choppy when dragging windows) I have tried to reconfigure x, making sure the ATI proprietary driver was turned on, and followed the ATI & Compiz known problems thread, none have worked. I tried metacity --replace and that has helped but everything is still running much slower than i know it should be. I was wondering if anyone else has encountered this problem and any known fixes

Thanks

pmgr33r,
Hi, I'm having the same issues.  I've got a X300 card and it does the exact same thing with the slow screen updates, scrolling and just slowness in general.  I've tried to run without effects, disabling the ATI graphics driver and various other attempts at reconfiguring xorg.conf.  Under 7.10 my system hummed along with no problems, under 8.04 it is unbearable.  

I am dumping my system and reloading 7.10. I hate the prospect of having to completely reconfigure my system but the time spent doing this is more acceptable than staying with 8.04.

Good Luck,
Finchair

---

### Post by d-mart on 2008-05-10
When I upgraded I had the same problem when i uninstalled xserver-xgl then my system now runs a lot better.  So if you have XGL installed then this could be the problem.  

Also as far as firefox 3 goes it seems to still have a lot of bugs cause it would cause my cpu to skyrocket so now I am using Opera till the final release.

I also have a x300 so i hope this helps

---

