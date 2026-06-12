---
title: "gtk-gnutella has stopped receiving data!"
date: 2007-08-03
forum: General Help
---

### Post by Giggity on 2007-08-03
For almost a year now, gtk-gnutella has given me unbelievably awesome service.  I double-click a file in the search window, and in less than a minute, the file I asked for has completed.

For the past few days, however, gtk-gnutella seems to have shut down all functionality.  I can still search for a file, and I'll still get numerous results, but when I double-click on the file, it goes to the "downloads" section, and sits there without receiving a single byte, regardless of how many people are offering it.

The most frustrating part is that I know other users are attempting to send me pieces of these files, because the red bar in the downloads section has little pieces that turn yellow for a second, the way they would back when the service worked.  But alas, a second after they turn yellow as if the transfer will begin, it turns red again.

It looks like something in my computer is rejecting the connections that other clients are making to my computer.  The ports are forwarded properly (if the sunglasses-smiley-face icon 8-) is a proper indicator), and bittorrent and donkey transfers still work as well as ever.  This never happened for the longest time, and now, no matter what I try to get through gtk-gnutella, it won't come through!

And here's the most annoying part:  Frostwire still works (it uses the gnutella network, right?).  But gtk-gnutella is vastly superior as far as my tastes are concerned.  Anyone have any ideas as to what is going on?  Is anyone else even having a similar problem?

All assistance and/or sympathy will be greatly appreciated!

---

### Post by cbiere on 2007-08-04
If you see the smiley, your forwarding configuration should really be fine. It is possible that something always drops the connections after the handshake though. So there could be "false-positives" under such weird conditions.

What version of gtk-gnutella do you use?

At the downloads pane, can you see in the status column what's reported for the connection? For example, do they all read as "Connection reset by peer" or what status do they show?

You might have to untick all "auto clear stopped download" toggles under "Settings" so that the status isn't cleared immediately but kept so that you can read it. Don't forget to enable them again later as it will use much more resources if you keep all those around.

---

