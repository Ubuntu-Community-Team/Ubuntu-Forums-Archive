---
title: "Youtube not working on midori/Qupzilla"
date: 2015-10-28
forum: General Help
---

### Post by sebastiaan5 on 2015-10-28
Hello,

I'm using lubuntu on an acer aspire one (intel atom, 4gb ram).

As I am using a light weighted OS I also want to use a light weighted browser, but I have problems with youtube in them.
Videos won't load in these browsers, I always get the error "An error occurred...".

I installed the additional repo's and flashplayer.

```
[COLOR=#000000][FONT=monospace]sudo apt-get install flashplugin-installer[/FONT][/COLOR]
```
[COLOR=#000000]```
[FONT=monospace]sudo apt-get install nspluginwrapper[/FONT]
```
[/COLOR]
Anyone know how to fix this?


greetings

---

### Post by sebastiaan5 on 2015-10-28
The thing is after a few times refreshing the page it works, I see the video and no more errors.
I've tried to fully reinstall midori but nothing...

---

### Post by Yellow Pasque on 2015-10-28
I'm running an Ubuntu 15.10 VM and youtube seems to be running just fine on midori there. youtube uses html5 now, so you shouldn't need to concern yourself with flashplayer. Heck, I'm not even sure youtube offers the old Flash interface anymore.

What version of Ubuntu and midori are you using?
What GPU and driver are you using?
Do you have gstreamer1.0-vaapi package installed (IIRC, it can cause issues with some GPU's).
Have you tried starting midori from the terminal and seeing if you get any error messages when failing to play a video?

---

### Post by sebastiaan5 on 2015-10-29
lubuntu 15.10
midori 0.5.11

Intel atom Inside
I don't think I have gstreamer

I see nothing specific in the terminal when trying to load a yt video.


thx for the reply :)

---

