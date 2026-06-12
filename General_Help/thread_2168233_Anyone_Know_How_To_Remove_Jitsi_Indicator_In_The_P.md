---
title: "Anyone Know How To Remove Jitsi Indicator In The Panel?"
date: 2013-08-17
forum: General Help
---

### Post by JosephBeck on 2013-08-17
Panel indicators are kind of useless to me and I usually turn them off on everything except system, time, sound, wifi and battery. Jitsi however doesn't seem to have a default indicator removal option like the rest. Any way to remove it? I run things from my launcher and if i close it from my launcher I want it to be actually closed and not running up top as an Indicator. Plus the indicator doesn't really mesh well with my color scheme xD.  Thanks to anyone that knows how to remove the annoyance (at least in my opinion). If not I'll just have to deal with it. I only added Jitsi so I could use video chat which pidgin doesnt have.  Using Ubuntu 13.04.

---

### Post by JosephBeck on 2013-08-17
Bump since this got barried. If it can't removed, it would be nice to at least make the background transparent.

---

### Post by kostkon on 2013-08-17
If it's a qt app, try removing the following package:
```
sni-qt
```
then restart your app.

It's 100% safe to do it, this particular package doesn't have any dependencies. All it does is to convert qt tray icons to indicators on the fly.

Hope that helps.

---

### Post by JosephBeck on 2013-08-17
Nope sadly didn't work v-v. Since I am installing Thunderbird I may re-enable to message indicator and I'm curious if Jitsi will remove its own indicator if that is activated. Not sure how Jitsi works but I know pidgin forced itself into the message indicator.  I tried to get onto their mailing list to attempt to get some support from them but so far haven't even received the acceptance email for the mailing list.    Edit: Didn't work what so ever. It placed Jitsi in the message indicator but once it started it opened into its own indicator. Managed to get to email the Developers even if it is awaiting moderation (unless your a mailing list subscriber you are apparently subject to moderation.  Seems like a bothersome process for anyone wanting quick and simple support).

---

