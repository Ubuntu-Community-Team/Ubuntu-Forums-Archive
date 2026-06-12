---
title: "Ubuntu 19.04 MSI laptop no sound through HDMI"
date: 2019-09-01
forum: General Help
---

### Post by bonej079 on 2019-09-01
Hi,

I have installed Ubuntu 19.04 on an MSI GS60 6QE laptop. Sound from  internal speakers is OK, but not through the HDMI connection. I have a  ViewSonic monitor with sound set to 100%, but I still cannot hear  anything from the monitor even though I set the HDMI for output in the  sound settings page. 

If I set the HDMI as the default sound output device and reboot, the monitor will not be detected. If I reset the output device back to speakers, then the second monitor is detected. 

Any ideas what I can do to solve this issue please?

Thanks,
JB

---

### Post by bonej079 on 2019-09-03
Any ideas please? Is this a bug or something to do with my hardware?

---

### Post by #&amp;thj^% on 2019-09-03
This is just a exercise in trouble shooting: [https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/](https://itsfoss.com/how-to-fix-no-sound-through-hdmi-in-external-monitor-in-ubuntu/)
And is there any other HDMI settings to chose from?
Also you need to set the right device in what ever Application your using.

---

### Post by bonej079 on 2019-09-08
Hi 1fallen,

Thanks for your interest in this post. Unfortunately still no sound :( In pavucontrol, I see that the volume bar is changing so sound is being "played" on the HDMI, but I can hear no sound. On the monitor, sound is set at 100%.

Regards
JB

---

### Post by #&amp;thj^% on 2019-09-08
Can you try a different source, rather than your Monitor?
A TV perhaps?
EDIT: Also in [Code Tags] show us this from the terminal:
```
xrandr --prop

```

---

