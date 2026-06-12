---
title: "Weird, seemingly unrelated, errors"
date: 2007-02-21
forum: General Help
---

### Post by Akegata on 2007-02-21
My problems started a few days ago, probably after I got my MX Revolution mouse.
The second day I had the mouse in question, ubuntu started freezing. It just dies, and sometimes it takes an hour for it to happen, sometimes it runs for several days.

Trying to figure out what was wrong (I really don't think it's the mouse that's causing the freezing..) I removed my creative audigy card right after the computer froze, as I'd had problems with it in windows before.
I enabled the AC'97 sound card on the mobo and booted the computer again.
When gnome started, I realized something had gone terribly wrong.

My font for all applications, except firefox, is not horribly ugly and almost unreadable.
My 3d acceleration was broken, because the symlink I hade made for /usr/bin/libGL.so.1 was replaced with another symlink. And the AC'97 sound card simply didn't work.

I rebooted, same problem. Put the audigy card back, replaced the symlink with the correct one, and I'm back to square one, except the fonts are still wrong.
So now my systems freezes every now and then for no apparent reason (I've been monitoring both syslog and messages with tail -f through ssh, nothing showed up when it froze the last time), and the fonts are almost unreadable.

The font problem is probably quite easily fixed, but the biggest problem I'm having here is that ubuntu goes crazy for me for no reason. That, plus I can't even begin to imagine how I should find out what's causing the freezing.

I guess this became more of a rant than a call for help, but I had to get it off my chest. I have been running Debian on different computers for four years or so, and I've never experienced problems like this on any of those computers. It's a shame too, I really like Ubuntu in all other aspects.

Any tips for what I can do to try to figure out what's causing my computer to lock up, or how to get the fonts back to default (or something even better) are highly appreciated.

---

