---
title: "Skype 1.4 starts at boot with an open window. Skype 1.3 started minimised."
date: 2007-06-17
forum: General Help
---

### Post by patslap on 2007-06-17
Hi

When I had Skype 1.3 I had it set up so that it loaded when the the desktop opened after bootup, and minimised itself to the panel.

Now I have upgraded to Skype 1.4 it loads up in a window on the desktop after bootup. 

I do not want it to leave a window open after boot; I only want a Skype logo in the panel.

Any ideas how to do this?


Thanks in advance. :p

---

### Post by patslap on 2007-06-19
bump

---

### Post by patslap on 2007-06-21
Is no-one else having this issue?

---

### Post by eustace on 2007-06-21
Apparently, there is no way to make it start minimized to tray. There is a bug addressing this issue, which you may want to track: [https://developer.skype.com/jira/browse/SCL-87](https://developer.skype.com/jira/browse/SCL-87).

There used to be a way to minimize the Skype window via its API, but alas this doesn't work with version 1.4, see here: [http://forum.skype.com/index.php?showtopic=88160](http://forum.skype.com/index.php?showtopic=88160).

---

### Post by patslap on 2007-06-24
Thanks

I'm now tracking this issue and will post back if a fix becomes apparent.

---

### Post by nirpius on 2007-07-30
I have a related issue. I'm trying to find a way of stopping Skype loading at boot. I have also got 1.4. When I was running Ubuntu with Kubuntu libraries it didn't start automatically but now I've loaded Kubuntu properly from the ISO and downloaded Skype and it starts at boot.

I've looked through Skype's Options and can't find anything there. Also, there's no reference to anything Skype (that I can see) in /etc/rc5.d or any other of these rc folders either. Does anyone know where I can find out how to stop this?

Many thanks

---

