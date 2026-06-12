---
title: "Laptop boot time issues"
date: 2006-12-29
forum: General Help
---

### Post by Max Spain on 2006-12-29
Greets folks, I just upgraded my Z71V laptop from 6.06 to 6.10 and I am having a lovely time getting things how I like them.  The reason I am making this post is because I am experiencing a problem I have never even heard of before.  

My laptop takes longer to boot when it is plugged in than when it is on battery power :eek: :confused: 

I found it really hard to believe at first, so I did a google search and a forum search.  For the first time they both failed me.  I did find an enlightening forum post describing the wonders of bootchart and from the output of that program I have definitive proof that my laptop takes longer to boot on AC power.  It isn't just a few seconds either.  Using battery power my laptop took 32 seconds to boot.  Using AC it took 1 min 21 seconds :-k   I am providing the bootchart output images just in case anybody here can make sense of them and tell me how to fix it.

Also if any of you are feeling generous here are some other problems I am working on:
Lost mouse double-clicks:  First click works fine, second one has a 1 in 4 chance of working ](*,)   Using standard synaptic touchpad.  Didn't happen with 6.06 or 5.10.
Browser plugins:  I tried using flash with firefox and got lots of crashes.  That problem is now fixed.  During that time I decided to try Opera and now for the life of me Opera can't find the mozilla flash plugin :-k 

Bootchart images:
First using battery powah:
[http://img367.imageshack.us/img367/1641/edgy200612291batteryqc9.png]("http://img367.imageshack.us/img367/1641/edgy200612291batteryqc9.png")
Second using ac:
[http://img292.imageshack.us/img292/7012/edgy200612292acwl9.png]("http://img292.imageshack.us/img292/7012/edgy200612292acwl9.png")
Any help would be appreciated :cool:

---

### Post by shane2peru on 2006-12-29
Wow, that is really an interesting dilemma.  I too have a laptop.  I really don't know what to tell, you about that.  I will time my boot ups next time I reboot and see if it there is any difference from Battery to AC Power.  As far as your upgrade problems, that upgrade was very disasterous for me.  I ended up having to completely re-install edgy from a clean slate.  Here is my xorg.conf from the synaptics part:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
### My added options
        Option          "LeftEdge"              "1700"
        Option          "RightEdge"             "5300"
        Option          "TopEdge"               "1700"
        Option          "BottomEdge"            "4200"
        Option          "FingerLow"             "25"
        Option          "FingerHigh"            "30"
        Option          "MaxTapTime"            "0"
        Option          "MaxTapMove"            "0"
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "0"
        Option          "MinSpeed"              "0.09"
        Option          "MaxSpeed"              "0.18"
        Option          "AccelFactor"           "0.0015"
        Option          "SHMConfig"             "on"


EndSection

```  Try plugging that in, and see if that helps.  There is a bunch of added on stuff that I stole/borrowed form someone else's config file, and it makes my touchpad scroll nicely now.  Well, at least it did.  I just checked it, and it quit for some reason?  Hope that helps a little anyway.

Shane

---

### Post by Max Spain on 2006-12-29
Thanks for the reply.  Your mouse settings strike me as being specific to your setup (except for MaxTapTime) but I'll look into it.

---

