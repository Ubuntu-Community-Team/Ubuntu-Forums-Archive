---
title: "External VGA/HDMI monitor or videoprojector out of sync"
date: 2016-11-25
forum: General Help
---

### Post by henkeldg on 2016-11-25
Hello to all,

I found what seems to be a previous mention of this problem over [here]("https://ubuntuforums.org/showthread.php?t=2320697&highlight=external+monitor"), but I decided to start a new discussion as the other one is tagged "[SOLVED]" whereas the so-called "solution" doesn't actually resolve anything as far as I can see.

For 3+ years I've used first Xubuntu then Lubuntu with various laptop computers and videoprojectors or external monitors on a regular basis to do slideshow presentations.  Although I now see that some people in the past had difficulties using Lubuntu with external monitors, this was never a problem for me (until now).  All I had to do was 1/start up the computer, 2/login, 3/attach VGA or HDMI, 4/log-out, 5/log-in again and everything was ready to go -- the projector was synchronized with my laptop screen.

Lately, however, I've experienced what I consider to be a serious regression in 16.04 and later updates of 14.04: when I go through my old routine the external projector merely shows the Lubuntu background and I have to turn off my laptop screen (System Tools > System Monitor) to show others what I'm talking about.  NOT convenient at all.

After playing around with xrandr, I realized that, in fact, my computer is creating a double-wide screen area, the left half of which is shown on my laptop, and the right half of which is sent to the external device.  For example, if I run my mouse pointer over to the right edge of the laptop screen it starts to show up at the left margin of the VGA or HDMI screen.  I can also drag windows back and forth from one to the other, but can't show them on both at the same time.  I tried running "xrandr --output HDMI-0 --pos 0x0" as a fix, but it only worked properly on one external monitor, whereas with others either the laptop display or the external one or both are off-center, and only show about 2/3 of the workspace.

The problem doesn't seem to be specific to LXDE as it also occurs with Ubuntu 16.04, and with later releases (14.04.4) of Lubuntu.  Downgrading to Lubuntu 14.04.1, however, allows me to synchronize the laptop and external displays as before.

Although I can imagine that some people might want to set two screens side-by-side in order to create an extra-large workspace, I rather question whether this really ought to be the default behavior (does anyone know if this was an intentional change or an inadvertent bug?).

All I really care about, though, is being able to synchronize my laptop screen with an external display on 16.04, as I don't intend to keep 14.04.1 for the rest of my life.

Any suggestions?

---

### Post by kingneutron on 2016-12-01
--Try installing package ' arandr ', it has helped me in the past with configuring monitors - and you can save settings as shell scripts. Post back if you have any questions or if this helped to resolve your issue.

---

### Post by henkeldg on 2017-02-01
I found the solution (it couldn't be simpler).  Just use Preferences > Monitor Settings, and adjust the resolution as needed according to the external screen/projector.  I guess this is something that either didn't exist or didn't work properly in the past, as I had become totally accustomed to my Login/Logout workaround.  Workaround no longer necessary.

---

