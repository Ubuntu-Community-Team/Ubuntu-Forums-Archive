---
title: "Need help refreshing Missing device nodes in /dev"
date: 2007-05-15
forum: General Help
---

### Post by prozacgod on 2007-05-15
I've been away from my desktop here at an office I work parttime in, and when I get back today, I am greeted by the familiar ubuntu login screen, when I logged in my desktop did not show up.  It took me a while to figure it out, but it seems that eth0 and lo are both missing in /dev  there are probably other device nodes missing as well - how do I refresh the /dev folder to get it back to the default - I've never enabled any graphics or audio or had to mess with files in this folder so it should be in a default configuration..

Thanks for the assistance.

-David

EDIT: I'm running Edgy Eft

EDIT: Okay, I've been looking arond and it seems to me that linux no longer uses /dev/eth0 or /dev/lo they are all under /dev/net well under /dev/net all I have is a tun device.

---

