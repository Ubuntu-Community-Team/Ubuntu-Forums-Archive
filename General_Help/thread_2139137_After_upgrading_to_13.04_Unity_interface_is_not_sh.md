---
title: "After upgrading to 13.04 Unity interface is not showing"
date: 2013-04-26
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2013-04-26
I've upgraded to Raring last night. The upgrade itself went okay, no errors. But when I rebooted the computer afterwards and logged in to my Unity session, all I could see was the Desktop background (together with Desktop icons), and no Unity interface. The Super button shortcut wasn't showing the Dash, there was no top panel etc. Please see the screenshot.
[IMG]http://i.stack.imgur.com/vFT6f.jpg[/IMG]
As a hint, I'm suspecting it's got something to do with my switchable graphics. I'm running Ubuntu on Acer Aspire AS5830TG with nVidia GT540M and an Intel integrated card. In 12.10 I was using Bumblebee to manage the graphic card switching. During the upgrade I saw something related to nvidia had to be uninstalled, but didn't pay much attention to it. I can't be sure if it has anything to do with my problem though.

What could possibly go wrong?

---

### Post by Giantmundo on 2013-04-26
I have the exact same experience.  I don't have anything special as you mentioned.  I suspect something related to nvidia cards.  The 12.10 upgrade gave me trouble with nvidia drivers and I suspect a similar story yet again but then I have read about a kernel bug may be the culprit.  If it is nvidia do we move back to an older driver or what.  At the moment I am going to just wait for a kernel update and hopefully it will come through tomorrow.  The graphic troubles with upgrades is doing my head in.  Bring on the rolling release.

---

### Post by Giantmundo on 2013-04-26
I was wondering if anyone thought this post was in anyway related to this problem.

[http://ubuntuforums.org/showthread.php?t=2138590]("http://ubuntuforums.org/showthread.php?t=2138590")

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2013-04-27
Giantmundo thanks for the input. I don't think that's the same problem as mine, since I'm able to get the login screen, and I do see my Desktop. It's the surrounding Unity 'chrome' that's missing. Anyway, I've tried installing linux 3.9 kernel as mentioned in the thread, but I got an anresolved dependancy error message.

---

### Post by Thee on 2013-04-27
Try this. It worked for me:
[http://ubuntuforums.org/showthread.php?t=2136435&page=2&p=12608396#post12608396](http://ubuntuforums.org/showthread.php?t=2136435&page=2&p=12608396#post12608396)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2013-04-27
Dang I hate when this happens. Somehow everything's back to normal. I've been fiddling around with my system, installing some drivers, uninstlaling some kernels, I actually have no idea what exactly was it that I did that fixed it. I remember deleting /etc/X11/xorg.conf and renaming /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf which fixed a few things, but not all. Now I wouldn't try to explain the rest because I'm simply not able to explain in a non-confusing way. I hope the rest of you guys with the same problem will find your way around this.

---

### Post by dino99 on 2013-04-27
probably that faulty compiz

dconf reset -f /org/compiz/
compiz --replace ccp &
setsid unity

---

### Post by Giantmundo on 2013-04-29
I found this suggestion and it worked for me.

Open a terminal (ctrl alt t) and execute ccsm. This will bring up the Compiz Config Settings Manager. Scroll down till you see the Ubuntu Unity Plugin. Click on it and then disbale it by unticking the Enable Ubuntu Unity Plugin checkbox to the left. Then re-enable it and you should get a series of conflicts resolve. Answer the questions so that Unity gets what it needs and then you should be OK. You may have to logout and in again.

---

