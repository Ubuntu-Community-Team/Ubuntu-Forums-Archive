---
title: "Chromium and Youtube"
date: 2020-11-16
forum: General Help
---

### Post by yapidumoac on 2020-11-16
Trying to watch youtube videos under Chromium and there are continual pausing, buffering and stuttering. Yet the exact same videos play perfectly well under [MPV]("https://mpv.io/"). Why is it so difficult for the Chromium developers to make a browser that can play a video.

---

### Post by CelticWarrior on 2020-11-16
It isn't difficult and as a matter of fact chromium-dev is the only browser in Linux that can enable hardware acceleration in Linux.
What you're experiencing is probably the result of playing 1080p60 (60 fps) videos in an entry-level CPU/GPU combo. MPV uses hardware acceleration so it works fine, that's all.

[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

---

### Post by TheFu on 2020-11-16
> **yapidumoac said:**
> Trying to watch youtube videos under Chromium and there are continual pausing, buffering and stuttering. Yet the exact same videos play perfectly well under [MPV]("https://mpv.io/"). Why is it so difficult for the Chromium developers to make a browser that can play a video.

I don't see that, but I only watch a few videos a week directly in the browser. I specifically use Chromium for youtube stuff, running inside a firejail. The exact version currently installed is this:
```
sudo apt search chromium-
Sorting... Done
Full Text Search... Done
chromium-browser/xenial-updates,xenial-security,now 86.0.4240.75-0ubuntu0.16.04.1 amd64 [installed]
```

I also have ```
chromium-codecs-ffmpeg/xenial-updates,xenial-security 86.0.4240.75-0ubuntu0.16.04.1 amd64
``` installed.
Works on a Core i5 laptop, inside a virtual machine and on a minimal GUI Ryzen with a cheap nVidia GPU. Note that I'm not using the snap version of chromium. I haven't figured out how to make snaps work in my setup. They refuse to run almost always.

---

### Post by yapidumoac on 2020-11-16
@CelticWarrior

Interesting, thanks for the response. What do you make of this and see attached graph of my so-called &#8220;broadband&#8221; connection.
-------

$mpv [https://www.youtube.com/watch?v=9aXLlMyFr70](https://www.youtube.com/watch?v=9aXLlMyFr70)

AV: 00:15:43 / 00:48:04 (33%) A-V:  0.000 Dropped: 41 Cache: 533s/150MB

[ffmpeg] tls: Error in the pull function.

[ffmpeg] https: Will reconnect at 355530096 in 0 second(s), error=Input/output error.

AV: 00:16:15 / 00:48:04 (34%) A-V:  0.000 Dropped: 66 Cache: 525s/150MB

[ffmpeg] tls: Error in the pull function.

[ffmpeg] https: Will reconnect at 19201904 in 0 second(s), error=Input/output error.

AV: 00:38:28 / 00:48:04 (80%) A-V:  0.000 Dropped: 929 Cache: 552s/150MB

[ffmpeg] tls: Error in the pull function.

[ffmpeg] https: Will reconnect at 36011760 in 0 second(s), error=Input/output error.

AV: 00:48:03 / 00:48:04 (100%) A-V:  0.000 Dropped: 1413 Cache: 0.0s
-------

[IMG]https://i.ibb.co/3N2H41k/speed.jpg[/IMG]

---

### Post by TheFu on 2020-11-16
There are 2 popular TLS libraries on Linux.  Google seems to use a different one than Canonical uses to build the FFMPEG program.  For chromium, there is an ffmpeg package addon which bridges the browser to ffmpeg for playback.

That's my guess.

I've seen instructions for building ffmpeg using the other TLS library. Since the connection doesn't always fail and sometimes works if I wait a few minutes and try again (I suppose the youtube servers have different LTS systems), it isn't a huge issue.  [https://forums.gentoo.org/viewtopic-t-1061342-start-0.html](https://forums.gentoo.org/viewtopic-t-1061342-start-0.html) tries to explain.

---

