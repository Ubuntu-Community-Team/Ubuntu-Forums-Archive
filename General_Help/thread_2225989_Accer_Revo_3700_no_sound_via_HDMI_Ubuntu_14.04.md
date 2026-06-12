---
title: "Accer Revo 3700 no sound via HDMI Ubuntu 14.04"
date: 2014-05-24
forum: General Help
---

### Post by nick114 on 2014-05-24
Hi All,

I have recently upgraded (clean install) my Accer Revo 3700 to Ubuntu 14.04. So far everything is working with the exception of sound over HDMI. This is my media-pc so this is a fairly big problem for me! :)

I used to run 10.04 and managed to get everything working by following a guide here:

[http://www.tuqix.org/wordpress/?p=252](http://www.tuqix.org/wordpress/?p=252)

Essentially, all I have done is:

```

[COLOR=#333333][FONT=Georgia]sudo vi /etc/asound.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]pcm.pulse {[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]type pulse[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]}[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]ctl.pulse {[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]type pulse[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]}[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]pcm.!default {[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]type pulse[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]}[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]ctl.!default {[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]type pulse[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]}[/FONT][/COLOR]

```

And added the following to [COLOR=#333333][FONT=Georgia]/etc/pulse/default.pa

```

[/FONT][/COLOR][COLOR=#333333][FONT=Georgia]load-module module-alsa-sink device=plughw:1,7[/FONT][/COLOR][COLOR=#333333][FONT=Georgia]

```

This did the trick last time (10.04) but saddly no luck with 14.04. I searched this forum and found a similar thread suggesting the same but it was also for 10.04.

Strangely, I can play sounds with the following:

```

[/FONT][/COLOR]**aplay** -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav

```

But if I try and watch a Youtube video through Firefox, I won't get any sound at all.

I run XBMC on this machine, I get GUI sound effects (i.e. scrolling through menus) but no sound in Movies.

Does anyone have any idea what the problem could be?

I think alsamixer looks strange in that it's missing the PCM channel that is visible in the screenshot in the guide I linked to above...

[[img]http://s23.postimg.org/a4zoldg2v/Screen_Shot_2014_05_24_at_18_17_41.jpg[/img]](http://postimg.org/image/a4zoldg2v/)

I don't know if this is related or not though.

Any help would be much appreciated, I miss watching movies on my HTPC!!!

Thanks, Nick

---

### Post by nick114 on 2014-05-24
OK, I've fixed this now. All I had to do was go into Settings -> Audio and select the HDMI output device. Things really have come on since 10.04!

---

