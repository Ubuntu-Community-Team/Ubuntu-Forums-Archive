---
title: "1024 768 Desktop Moves Around"
date: 2007-02-06
forum: General Help
---

### Post by hhh on 2007-02-06
Checking out Ubuntu using the Live CD. Very impressive. I've got my 3 button mouse working using Xorg, but when screen resolution is set to 1024x768, the desktop is larger than the screen and shifts around when I place my mouse at far top/bottom/left/right of the screen. Is there a way to fix this? My monitor is an AOC 7Elr w/ a horizontal refresh of 30-70hZ. I followed the configuration instructions here...

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

On the plus side, I've been able to easily update to Firefox 2.0.1 in under 10 minutes using the instructions here (Option 4)...

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

... and enabled mp3 playback by installing XMMS as suggested here...

[http://www.beginningubuntu.com/dapper_tips.html#Install_XMMS_the_old-school_MP3_player](http://www.beginningubuntu.com/dapper_tips.html#Install_XMMS_the_old-school_MP3_player)

Thanks for the help.

---

### Post by hhh on 2007-02-06
bump

---

### Post by disturbedite on 2007-02-06
i've ran into this problem before when wine exits (prematurely) a program that was running in full screen at a resolution different from the desktop.  i also get it from kdm, the login screen manager program, i don't know how to solve the kdm issue tho.  i wish there was just a config file i could just edit.  (maybe there is?) 

as far as the desktop issue is concerned, i solved it very easily.  all i had to was change the desktop refresh rate.  apparently kde doesn't correctly detect which resolutions/refresh rates my monitor is capable of displaying along with what my video card supports.  (yes i have my specific monitor/video card specified, not generic ones).

---

