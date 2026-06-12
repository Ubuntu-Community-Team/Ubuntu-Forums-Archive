---
title: "Screensave comes on during movies..."
date: 2007-09-11
forum: General Help
---

### Post by CD Baric on 2007-09-11
Why is the screensaver not automagically disabled during movies or TV?

Anybody have a solution?

CD Baric

---

### Post by girishv on 2007-09-11
That depends on what are you using to play the video. If you are using mplayer for example, using 
-stop-xscreensaver
stops the xscreensaver during the play and re-starts it on exit

Girish

---

### Post by tszanon on 2007-09-11
I've used both gxine and totem. When playing videos in fullscreen, the screensaver never comes up.

---

### Post by CD Baric on 2007-09-12
> **girishv said:**
> That depends on what are you using to play the video. If you are using mplayer for example, using 
-stop-xscreensaver
stops the xscreensaver during the play and re-starts it on exit

Girish

Thanks Girish, I made the following entry in my /etc/mplayer/mplayer.conf

stop-xscreensaver=yes

and now when I watch movies using mplayer and smplayer the screensaver doesn't start.

Any idea how to create the same effect with tvtime.

Regards,

CD Baric

---

### Post by CD Baric on 2007-09-12
> **tszanon said:**
> I've used both gxine and totem. When playing videos in fullscreen, the screensaver never comes up.

How about tvtime?

Thanks,

CD Baric

---

### Post by QwUo173Hy on 2007-10-08
The screensaver doesn't come up for me with totem either, but the power management component of the screensaver utility doesn't get disabled, so my screen goes black after 40 minutes. Any ideas how to fix that?

---

### Post by Shazaam on 2007-10-08
> **jarlath said:**
> The screensaver doesn't come up for me with totem either, but the power management component of the screensaver utility doesn't get disabled, so my screen goes black after 40 minutes. Any ideas how to fix that?

Don't quote me on this as I haven't tried it yet, copy and back up your xorg.conf (I don't have  the code right at hand) and then comment out DPMS (in section "Monitor") as an experiment.

---

