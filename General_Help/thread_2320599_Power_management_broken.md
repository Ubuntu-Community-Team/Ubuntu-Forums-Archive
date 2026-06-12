---
title: "Power management broken?"
date: 2016-04-15
forum: General Help
---

### Post by jebediah on 2016-04-15
Currently i'm running Ubuntu Trusty + XFCE at a Dell Chromebokk with Crouton. Everything "at lest after a couple hours trying" works as it should and i'm happy with how smooth it is.
But......Power management seems to be broken some how and it has no effect what so ever.
If i leave the chromebook alone the brightness goes down to about 60% after 40 sec, and 10 sec later the screen goes black. The thing is, i've set almost all of the power management setting to about 10 min or so except the screen saver, that one is set to 3 min.

Also i noticed that sleep/suspend when lid is closed doesn't work. Thoose options are not even in the options. I only have Nothing or Screen lock

Sorry for my lack of English and my poor knowledge when it comes to Linux :)

---

### Post by TheFu on 2016-04-15
Dell chromebooks may be different - I have an Acer and Toshiba chromebook, so this is based on that experience.  Never used crouton on the Acer, but have been running crouton on the toshiba since mid-January.

A chroot, like crouton, isn't the same a running full virtualization.  I think anything inside crouton that touches hardware shouldn't be used as a general rule.  The hostOS (chromeOS) needs to handle the hardware.  That applies to power, screen, audio, portable disks, networking,  ... 

Power management should be handled by ChromeOS, at least that is how I'd do it. You can enable and disable it in chromeOS, but not much more (well, since I run as guest, my options are limited). There is a chrome-browser app or you can do it from a shell.  I manually enable/disable power management on the chromeOS side when I don't want the overly aggressive desktop settings from ChromeOS to impact my more server-like use of Ubuntu side of the system.  

Screen saver settings related to power may or may not work, but how long it takes to be enabled should work, for the *buntu-side, provided the chromeOS side doesn't override it.

---

### Post by jebediah on 2016-04-17
Thanks :)
Think i underestimated the Chrome store. Got the app and the Chrome power management is now gone.

On to the next problem

---

### Post by jebediah on 2016-04-20
A small update on the power managemnt issue.
I've downloaded the [Keep Awake Extension]("https://chrome.google.com/webstore/detail/keep-awake/bijihlabcfdnabacffofojgmehjdielb") and it works great, but only when i'm watching a movie on VLC or Youtube.
It's strange, but here's what happens.

If a watch a movie either on VLC or Youtube, the monitor uses my rule from the power manager. But if i turn of the movie the only thing working is the screensaver.
Also sleep and suspension is still greyed out.

Don't know if i should try another Linux dist och maybe just change desktop enviroment.

---

