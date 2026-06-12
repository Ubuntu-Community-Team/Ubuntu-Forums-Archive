---
title: "sound blocking"
date: 2008-05-28
forum: General Help
---

### Post by pjkoczan on 2008-05-28
I'm running into a problem with sound on Hardy. Basically, sound appears to be exclusive to one program. For instance, if I visit a page in Firefox that has sound (even just a silly little flash thing), vlc will then have no sound when I try to run it until I close Firefox and re-open the video stream in vlc. Even when I try to run vlc from the command line no errors are spit out so I'm a bit lost as to what's happening.

I'm running off of onboard sound. I don't know offhand which motherboard I have but I can look it up if need be.

I didn't have this problem in previous Ubuntu installs. Any ideas about what I could do to fix this?

---

### Post by Zorael on 2008-05-28
Is this only an issue with firefox and other programs, or between any other program as well?

If firefox is the only culprit, you may want to install the [FONT="Courier New"]libflashsupport[/FONT] package.

---

### Post by pjkoczan on 2008-05-28
> **Zorael said:**
> Is this only an issue with firefox and other programs, or between any other program as well?

If firefox is the only culprit, you may want to install the [FONT="Courier New"]libflashsupport[/FONT] package.

As near as I could tell, it was firefox only.

libflashsupport fixed it perfectly. Thanks.

---

