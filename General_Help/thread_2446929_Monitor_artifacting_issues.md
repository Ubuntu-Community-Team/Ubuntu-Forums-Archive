---
title: "Monitor artifacting issues"
date: 2020-07-09
forum: General Help
---

### Post by iinuwa on 2020-07-09
Hello,

I am having some trouble with my monitors.I have a Lenovo P53 with an NVIDIA Quadro T2000 graphics card (with proprietary driver 440) running Ubuntu 20.04, connected to two 24" ViewSonic monitors through a the Lenovo USB-C docking station. 

Whenever certain colors appear on the screen, I get a weird "artifacting" issue. I'm not sure if that's the word for it; I haven't seen anything like it before. The monitors become unreadable, and for certain images, the monitor loses the connection altogether. If I change the image on the screen, or put my mouse in a certain position, it comes back again. I'm wondering if anyone has seen this issue and can help point me to some troubleshooting steps.

Video of issue: [https://photos.app.goo.gl/d2VcbjkvFdvYEb6n6](https://photos.app.goo.gl/d2VcbjkvFdvYEb6n6)

Some other things to note:
- I am running Regolith (i3 + GNOME) and have tried a couple of different compositors with the same result.
- I have used these same monitors with two different laptops (both using the nouveau driver) via DVI and VGA, but not DisplayPort, and it worked just fine.
- The nouveau driver doesn't support my graphics card yet, so I can't test that.
- The issue never happens on the laptop screen itself, only when connected to the monitors.
- This happened on Ubuntu 18.04, as well, and with NVIDIA driver versions 435 and 440 on both OS versions.
- There is an HDMI port on the laptop, but I've never been able to get that to recognize the monitors. Unfortunately, it seems that two DP connections are the only way I can get dual monitors.
- If I take a screenshot of the desktop while the artifacting is happening, the screenshot displays just fine. This leads me to believe that it's a problem with the monitors, or the connection to the monitors somehow.

Thanks for your help,

Isaiah

---

### Post by pqwoerituytrueiwoq on 2020-07-09
probably a bad cable or port on the monitor

---

