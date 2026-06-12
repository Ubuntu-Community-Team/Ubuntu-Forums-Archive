---
title: "Wengophone 2.1.1 window error"
date: 2007-10-14
forum: General Help
---

### Post by LordMau on 2007-10-14
I'm trying out VOIP options under ubuntu and in the process of testing Wengophone. It installed without fanfare from Gutsy's repos but when I start I always get this problem, see screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46280&stc=1&d=1192335059[/IMG]

What's happening is:

[LIST=1]
[*]There are no window border visible just white space where it should be.
[*]The window always opens at 2048 px width, though my desktop is set at 1024. I had tried to use the advanced setting menu under wengo, and also tried manually editing its config.xml file, but it always overrides what was written there and still opens at 2048px. In fact when I reopen the config.xml file it reverts back to a 2048 setting. I'm also unable to resize the window with the mouse, it's stuck at that width!
[/LIST]

I'm running this under fusion mainly, but I also tried plain non-Xgl xfwm and the same behaviour still exists. Any ideas how to fix this?

Thanks.

---

### Post by steefjeqv on 2007-10-19
Hi,

Same problem here.

Using 64 bit Gutsy + Nvidia 6200 + Compiz.

Greetings,
Steven

---

### Post by yang on 2007-10-20
same here, using 64-bit gutsy + nvidia 8300 gs

can't actually seem to connect, either (just says 'connecting')

---

### Post by peachy on 2007-10-20
this seems to be fixed in the 2.1.2 release, but then i have no sound through ALSA.

pretty disappointing really :-/

---

