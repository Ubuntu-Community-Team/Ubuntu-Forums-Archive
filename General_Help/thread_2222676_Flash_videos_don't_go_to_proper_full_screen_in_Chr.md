---
title: "Flash videos don't go to proper full screen in Chromium"
date: 2014-05-07
forum: General Help
---

### Post by halfbeing on 2014-05-07
Hello,

I've been having a problem with full screen mode in Flash videos in Chromium. I have read quite a lot of other people describing various problems with Flash and full screen mode, but I haven't found any that match what is happening with me.

This is what happens: I go to, say, [http://deredactie.be/cm/vrtnieuws/videozone](http://deredactie.be/cm/vrtnieuws/videozone) and pick any video and play it. I click on the full screen button. A window opens which takes up most of the screen with the video enlarged to fill it, but it isn't proper full screen in that the various window decorations and widgets are still visible. Also there are no play controls, which makes it impossible to navigate through the video.

I don't get this problem when I watch html5 videos on YouTube or Vimeo. Can this be fixed?

Thanks in advance.

---

### Post by zitelli-pablo on 2014-06-04
> **halfbeing said:**
> I've been having a problem with full screen mode in Flash videos in Chromium.

I click on the full screen button. A window opens which takes up most of the screen with the video enlarged to fill it, but it isn't proper full screen in that the various window decorations and widgets are still visible. Also there are no play controls, which makes it impossible to navigate through the video.

I have the same problem. Any ideas?

---

### Post by halfbeing on 2014-06-04
I realised after I posted my question that Chromium uses Pepper Flash rather than Adobe Flash Player. So it is a deficiency within Pepper Flash. Unfortunately Adobe Flash Player is no longer compatible with Chrome/Chromium (because Google decided to stop supporting the insecure Netscape plugin format). In other words I suspect we are stuck with this until Pepper Flash gets fixed.

---

### Post by RavanH on 2014-06-30
I noticed the same issue in Chromium today. Flash player full screen keeps showing window decoration (empty) title area, which forces the lower part of the video off screen. This explains the missing progress bar etc.

The issue is not there in Google Chrome. Difference probably lies in Pepper Flash version.

**Chrome:**
Shockwave Flash 14.0 r0
Version:14.0.0.125
Location: /opt/google/chrome/PepperFlash/libpepflashplayer.so
Type: PPAPI (out-of-process)

**Chromium:**
Shockwave Flash 13.0 r0
Versie: 13.0.0.182
Locatie: /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so
Type: PPAPI (out-of-process)

I'll test a simple replacement of the 13.0 with the 14.0 so file and report back...

---

### Post by RavanH on 2014-06-30
Nope... Starting Chromium with command 
```
$ chromium-browser --ppapi-flash-path=/opt/google/chrome/PepperFlash/libpepflashplayer.so
```
making Chromium use the libpepflashplayer.so provided with Google Chrome (must be installed, of course) does not solve the issue. 

The issue must come from somewhere else :(

---

### Post by RavanH on 2014-06-30
OK found it...

In your Chromium browser go to **chrome://flags** and find the flag **fullscreen-within-tab**. Enable it and relaunch the browser with the button that will appear at the bottom of the screen after changing any flags.

After that, the Flash player will be able to go truly full screen without any window decoration :)

---

