---
title: "Text Turns Blue While Scrolling"
date: 2013-12-19
forum: General Help
---

### Post by buzzingrobot on 2013-12-19
Text turns blue while I scroll in Firefox, in the RSS reader Liferea, and in Thunderbird.

Disabling smooth scrolling used to get rid of it, but no longer.

It's actually rather annoying.

I see it in any other distro I've used that runs Gnome or components of Gnome, like Unity.

I haven't seen it in KDE, even using the same app versions.

Anyone else seeing this?

(Ubuntu 13.10; Firefox 26.0; Thunderbird 24.2.0; Liferea 1.8.15; ThinkPad W530 with 1920x1080 screen on Intel video)

[Edit:  Happens in Chrome, too.]

[Edit 2:  Switched to the Nvidia  GPU and an Nvidia driver.  No change.  Switching back.]

---

### Post by tgalati4 on 2013-12-19
Any errors in /var/log/Xorg.0.log?  That is a strange problem.

Try using an external, wired, USB mouse and see if it does the same thing.  Perhaps you have an error in one of your input device files.  Have you made any mods to /etc/X11/xorg.conf?

Perhaps you have a stuck Left-Shift trackpad key.  Have you spilled anything on your keyboard lately?  I know thinkpads have drain holes, but the trackpad keys can still fail with too much beer.

Run *xev* and see if you are getting correct events:  You should see Button 1, Button 2, Button 3 as you press the left, middle and right mouse buttons.

---

### Post by buzzingrobot on 2013-12-20
No errors in the logs. It's apparent using both the touchpad and a mouse. (I usually use a wired USB mouse rather than the pad while at the desk.) XEV checks out, too.

It's mitigated if I turn off animation. I.e., less obvious on normal text, still obvious on bold text.

---

### Post by tgalati4 on 2013-12-20
So it is possibly a compositing error.  When you scroll, the screen needs to get repainted--constantly.  No errors in .xsession-errors?  No errors in Xorg.0.log?  I would suspect a problem with your graphics chip--specificially the video RAM or the 3D rendering engine.  Don't know if you can fix, but you can run a bunch of video tests:* phoronix-test-suite*.  You can probably narrow down the issue by going through the video tests.

It's possible that KDE gets around the issue by using a different compositing method or a different video RAM footprint, so the problem is not noticeable.

---

