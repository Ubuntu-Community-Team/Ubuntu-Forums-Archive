---
title: "Dead desktop -- help!"
date: 2015-05-24
forum: General Help
---

### Post by JKyleOKC on 2015-05-24
Unlike jonners's problem, I have a dead desktop after shutting down this system overnight. No updates appeared to be involved, however.

This machine normally runs 24/7 365 days/year, but last night I shut it down after severe weather in the area made power a bit flaky. At that time it seemed to be working well, although it did complain about the session manager being open and refused to shut down until I had closed all open files.

This morning upon powering it up I was greeted by a black screen although both top and bottom panels were showing properly and responding to events. The machine is configured for automatic login. I was able to log out and back in, and at that time my configured desktop background appeared but without any of the icons normally displayed, and it did not respond to any right-clicks on the desktop.

Searching for help here led me to jonners's posts and I then checked via Synaptic for nvidia drivers; it showed that the whole batch of them were upgradable, so I did upgrade them. It made no difference. Then running Software Updater showed that xfdesktop had an update, as did gvfs, so I ran those also.

The desktop, however, remains totally dead. the xfce-session directory in ~/.config is empty, and any restart now comes up with a gray (not black) screen instead of the chosen background. However, logging out and back in restores the background image.

I seek suggestions. It's apparently a configuration issue of some sort -- but where???

---

### Post by JKyleOKC on 2015-05-24
Interesting -- rebooting to an older kernel failed to fix things, but then when I returned to the current one, the desktop was working again!

Still no idea what made such a difference, but now that it's working I'll mark this solved. I'd still like to hear any ideas anyone else has, though. I don't trust such magical fixes -- they leave me suspicious that Murphy is still lurking behind the scenery!

---

