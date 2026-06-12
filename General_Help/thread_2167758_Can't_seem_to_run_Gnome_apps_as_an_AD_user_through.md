---
title: "Can't seem to run Gnome apps as an AD user through Likewise Open"
date: 2013-08-14
forum: General Help
---

### Post by GoTerpsGo on 2013-08-14
Hello,

Google seems to be stumped so I hope someone can help me with this seemingly esoteric problem...  I'm working on setting up a 13.04 VM instance that would SSO through my AD; I already have this working through Likewise Open.  I intend to use X apps tunneled to my Win7/OSX desktops; I've already done this previously many, many times.

That said, I can't seem to get Gnome apps to run.  I get the following message before the app dies:

** (gnome-terminal:14250): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I looked for a gnome error log but there doesn't seem to be such a thing.  Syslog doesn't tell me anything.  I'm certain it's Gnome-related because gnome-terminal and gedit fail with the same error, but xterm and eclipse run just fine.  Is there some kind of conflict between Gnome and AD or Gnome and Likewise that I'm not aware of?

Thanks,

 - Joe

---

