---
title: "Firefox not shutting down properly"
date: 2014-02-17
forum: General Help
---

### Post by Extreedoc on 2014-02-17
Firefox isn't shutting down properly, I have to kill it in System Monitor. It has happened twice this evening. I see that others have had this problem but those seem to be much older distros than mine.
I am running 12.04 and Firefox 27.0 on a 64 bit system. There are no add-ons and I haven't established a profile, it is exactly as it comes out of the box.
Earlier sufferers of this problem (4 years ago!) identified a bug in Ghostery but as I said: I have _No Add-Ons_.
If it helps, I had a similar problem with Compiz several days ago, that problem has not, so far, re-surfaced.

---

### Post by kurt18947 on 2014-02-17
I've had the same problem in the past but it was infrequent so I didn't really attempt to chase it down.  I'm running 14.04 Gnome and haven't seen it happen once.  I think the next Gnome LTS is stacking up like a good one for me at least.

---

### Post by tgalati4 on 2014-02-17
Delete your profile and firefox will create another.  It probably has some subtle corruption.  Try running* firefox --debug*  in a terminal and see if there are any errors that show up when shutting it down.

---

### Post by Extreedoc on 2014-02-18
Thanks both, I will consider what you have said.

A thought occurs: could I use Debugger from the Tools>Web Developer menu?

Edit: Damn thing has behaved itself since yesterday, I did delete the profile.

---

