---
title: "Cant find menu.lst"
date: 2008-05-12
forum: General Help
---

### Post by xeonicxpression on 2008-05-12
So I used Wubi to install Ubuntu and everything was going fine.  Last night I go to boot into Ubuntu and it tells me it can't find menu.lst.  I was confused since it was working a few hours earlier.  After trying each of the options to find menu.lst I just decide to boot into Vista.  It starts booting Vista then it tells me it needs to do a chkdsk.  At this point I was a little worried hoping that my hard drive isn't going out on me.  I open up the D drive to see whats up.  I find a hidden folder "found.000" and subfolder "dir0000.chk".  Inside there are my boot and shared folders and my root.disk and swap.disk files.  Do I just copy those back into the ubuntu folder?  Is this a sign of a failing hard drive or just some weird goofup?

---

### Post by ago on 2008-05-14
Yes that is due to unclean shutdow/fs corruption. You can try that, but it would be better to use some windows fs recovery tools. Do not ask me for suggestions though since I have no direct experience with such tools, I am a linux guy after all... :)

---

