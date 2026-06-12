---
title: "Ubuntu GNOME 13.04 doesn't perform action on critically low battery"
date: 2013-07-31
forum: General Help
---

### Post by fffree on 2013-07-31
I have an Acer Aspire One 725, running Ubuntu GNOME 13.04. I get a warning when the time remaining is 5 minutes, and it says it will shutdown or hibernate shortly if I do not plug in. However, about two minutes from that point the computer will just run out of power and crash -- the system never hibernates (which is the what I have set it to do, thought if this is set to shutdown it does not work either).

Subsequently, I found [this]("http://askubuntu.com/questions/167062/netbook-performs-hard-shutdown-without-warning-on-low-battery-power") and have adjusted the settings in org.gnome.settings-deamon.plugins.power so that it should take critical action at 5% remaining. I do get the warning in time again, but it does not appear to perform the hibernation action. Any ideas why this may not be working?

Many thanks in advance!

---

