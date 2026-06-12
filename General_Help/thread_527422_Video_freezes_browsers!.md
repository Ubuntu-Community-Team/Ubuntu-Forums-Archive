---
title: "Video freezes browsers!"
date: 2007-08-16
forum: General Help
---

### Post by Sparky222B on 2007-08-16
Hey,

In both Firefox and Konqueror, most video types just freeze the browser, including, but not limited to, Flash, WMV, Mpeg, and Avi.

---

### Post by o2blom on 2007-08-25
Same problem here, with Kubuntu 7.0.4. This seems like a fairly serious problem (once it happens I just power off the comp). Does anyone know what is going on ?

---

### Post by Sparky222B on 2007-08-26
bump

---

### Post by bluekage on 2007-08-26
I too am having the same problem, plus I am experiencing the same issue in external players as well. Any insight on this issue would be greatly appreciated.

---

### Post by Sparky222B on 2007-08-26
I also experience this in most external players

---

### Post by bluekage on 2007-08-26
Well, I've done a bit of digging around and I found [this]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287") which may help some people, unfortunately it did not work for me. I do believe that this is some sort of sound issue though, as opposed to video. If I open a file in VLC I can watch the video, but it won't play any sound and all the controls are frozen. If I try to close it I have to force quit. I also experience the same freeze when I try to play any songs.

---

### Post by ed67 on 2007-08-28
Bumping this topic because I have the same problem.  I don't know about other browsers but I use Firefox and it happens once in a while.  Usually for me it's when I close (try to close) the tab the video was playing in.  This can be as it's playing or after it's done, doesn't seem to matter.

I can force quit Firefox, and my system still operates, but when I try to restart firefox it says Firefox is already running but is not responding, blah blah blah, and I have to restart the computer.  Logging out and back in doesn't fix it.

---

### Post by SpectralDesign on 2007-10-18
this is still happening, apparently it's a bug in the flash engine:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/92207](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/92207)

it's annoying, to say the least.. at least firefox will restore a session these days when it gets wedged.  If I were a half decent coder I'd be working on fixing this myself, but I'm not. :mad:

---

### Post by SpectralDesign on 2007-10-18
okay, I have more information --

One workaround I saw posted was to disable sound -- seems like a poor choice, but then I found this:

```
The workaround seems to work on my system. What I do specifically is:

1. Open a new FireFox window.
2. Go to Youtube and select to open any random video.
3. Press pause so it doesn't reach the end.
4. Minimize that window.
5. Open a new FireFox window.
6. In the new browser, surf the net, watch videos, do whatever.

With at least one instance of Flash running in another FireFox window,
Flash does not crash.

Thank you for reporting this workaround. Though I hope Flash, FireFox,
or Ubuntu will eventually be resolved for so as not to have this problem
with Flash and hda intel sound drivers.

```

I haven't tried it yet, but there are several people saying it works.....

---

### Post by chameleonkid on 2007-10-18
I think I had the same problem. When I unchecked the restricted driver for my nvidia driver in the restricted drivers section, the problem seemed to disappear. I just installed envy and the nvidia driver, hopefully that fixes it. So I would say try unchecking the restricted driver and then running a video, just to see if that may be the problem.

---

### Post by Sparky222B on 2007-10-18
Since updating to Gutsy RC1, I've had no problems. An update to 7.10 fixed a lot of my other problems, too, such as HDA Intel problems with ALSA and RT2500 wireless issues.

---

