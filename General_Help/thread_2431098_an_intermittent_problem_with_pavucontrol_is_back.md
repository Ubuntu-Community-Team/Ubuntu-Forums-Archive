---
title: "an intermittent problem with pavucontrol is back"
date: 2019-11-11
forum: General Help
---

### Post by Skaperen on 2019-11-11
an _intermittent problem_ with [COLOR=#0000cd][FONT=courier new]**pavucontrol**[/FONT][/COLOR] is back.  when i had this problem before, it was not fixed until i _rebooted_.  the problem is that it is *not* showing any _audio activity_. i can change the audio level and i still hear the audio.  i shows the audio level setting, but it shows no  sound.  when i quit [COLOR=#0000cd][FONT=courier new]**pavucontrol**[/FONT][/COLOR] and restart it, it is still has the same problem.  this is just like when this problem happened before.  after i rebooted back then, it worked OK, again.  today i have not rebooted, yet, and decided it would be better to do more investigating before i do so.

it's a little bit different this time because i have [COLOR=#0000cd][FONT=courier new]**pavucontrol**[/FONT][/COLOR] running in 2 different users.  previously i didn't think of running it in a different user.  but, this might change the observation of the problem because the problem is happening under user [COLOR=#ff0000][FONT=courier new]**admin**[/FONT][/COLOR] and *not* happening under user [COLOR=#ff0000][FONT=courier new]**phil**[/FONT][/COLOR].  i have restarted it under _both_ and it remains broken under user [COLOR=#ff0000][FONT=courier new]**admin**[/FONT][/COLOR] and continues to work under user [COLOR=#ff0000][FONT=courier new]**phil**[/FONT][/COLOR].

further, under user [COLOR=#ff0000][FONT=courier new]**admin**[/FONT][/COLOR], where it is not working right, it shows an incomplete list of playback sources.  it does *not* include the firefox browser that is running under user [COLOR=#ff0000][FONT=courier new]**vid**[/FONT][/COLOR], which has accessed a [live radio feed]("https://www.youtube.com/watch?v=60UGcXAW0qM") on YouTube.  but under user [COLOR=#ff0000][FONT=courier new]**phil**[/FONT][/COLOR], the list is complete.  it's as if these were under 2 different systems, but they are both on the same one.  here are screenshots of these 2 instances of [COLOR=#0000cd][FONT=courier new]**pavucontrol**[/FONT][/COLOR] running.  these are PNG format of a 1920x1080 display.

[http://ipal.net/ubuntu/201911112118081160452365.png](http://ipal.net/ubuntu/201911112118081160452365.png)
[http://ipal.net/ubuntu/201911112120041613122224.png](http://ipal.net/ubuntu/201911112120041613122224.png)

any ideas what might be the cause?  any ideas of more places to check?

---

