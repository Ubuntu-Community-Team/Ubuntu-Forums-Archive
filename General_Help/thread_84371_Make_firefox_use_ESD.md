---
title: "Make firefox use ESD"
date: 2005-10-30
forum: General Help
---

### Post by Joh_ on 2005-10-30
Everybody seems to have trouble with flash and ubuntu, even though my question differs from many.

I just got it working through [this thread](http://ubuntuforums.org/showthread.php?t=75237) (the 2nd solution since the first wouldn't work). But since aoss and anything alsa gives me VERY loud sound output with no way to change it (lack of support), and esd seems to give me decend sound volume with all apps that support it (all apps I generally use), my question is; is there any way I can make flash use esd for output? Just so I won't have to get such loud "noise".

Thanks in advance!

---

### Post by Nomad64 on 2005-10-31
I believe FlashPlayer will try to use the default sound system specified by Ubuntu. Goto System -> Preferences -> Multimedia Systems Selector, and make sure that the default sink output setting is set to use ESD.

I remember having flash sound problems in both Horay and Breezy (mostly Horay), but I was able to solve them, and now flash works fine for me.

Also, in the thread you specified, did you try setting FIREFOX_DSP to "esd" instead of "aoss" or "auto"? I am kind of shooting-in-the-dark here, but it can't get any worse, right? =P Plus, if it does make it worse, you can just change it back without harm.

---

### Post by Joh_ on 2005-10-31
Hmm.. When I check System > Preferences > Multimedia System Selector, it says it's set to ESD so I believe it is. :p Also I've tried to set it to "esd", "libesd" and "esound". All without success. ](*,)

---

### Post by Joh_ on 2005-11-09
Finally solved it! (Not that I was trying too hard though :p)

I solved it by first backing up my /usr/bin/firefox file. Then copy /usr/bin/aoss and naming it firefox and thus replacing the old one. Then I modified it slightly, gave it executable rights, and all work well now. I've got all firefox sound going through esd. :D

Might try with java later. I've made it with one app though, by using a start script starting "aoss java -D.... etc".

---

