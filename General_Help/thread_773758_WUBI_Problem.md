---
title: "WUBI Problem"
date: 2008-04-29
forum: General Help
---

### Post by The Ruckus on 2008-04-29
I am running Windows Vista, and am having a bit of a problem with WUBI. I downloaded the setup, installed, chose Xubuntu and set my user name and password. All went well, but when I boot my PC will not prompt me with the ability to boot with Ubuntu. When I hit F12 for the boot menu I see no such thing. The WUBI page says it's known to work with Vista, so what am I doing wrong?

---

### Post by Vermind on 2008-04-29
Hello,
Maybe You need to hit F8. At least in XP, F8 is used to bring up the "safe boot" menu. 
The option to boot Ubuntu should show up beside Vista when booting normally, without pressing anything, though. 
Have You changed Vista boot parameters? I think there is an option for a timeout before starting Vista. If this is too low You might not be given the choice.

---

### Post by The Ruckus on 2008-04-29
I have not changed anything, how would I go about checking to see if this boot up time is too short?

---

### Post by Vermind on 2008-04-29
Hello,
I don't remember exactly, I don't use the Vista on my laptop very much. Something to do with control panel system and startup or boot options.
I found this while searching for the boot options:
[EasyBCD freeware vista boot manager]("http://neosmart.net/dl.php?id=1"). I didn't try it, but it sounds like it would allow You to add the entry to boot Ubuntu if wubi failed about it.
You should google up what a Windows bootloader Ubuntu entry looks like.

---

