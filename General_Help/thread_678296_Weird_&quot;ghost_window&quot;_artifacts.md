---
title: "Weird &quot;ghost window&quot; artifacts"
date: 2008-01-25
forum: General Help
---

### Post by jeddhor on 2008-01-25
Hi guys!

I think this is my first actual post, so bear with me.

I'm using the newest Ubuntu (7.10) and so far everything has worked great, except for some gDesklet issues, but that's not the reason I'm posting.

I'm getting these weird graphics errors sometimes.  They're not really "errors" per-say... What happens is when I minimize or restore a window, or start a new program that opens up in less than full-screen size, sometimes I get a "ghost image" artifact, that looks like the window that just opened/moved (but sometimes is larger, as in it is zoomed in but still a copy of the same window that just moved) that appears somewhere in the background on my desktop, usually just behind the window that it is mimicking.  The image goes away if I move a window over top of it.  It's not a show-stopper for me... it never gets in the way, and I can always get it to go away by moving something over top of it to refresh the screen underneath.  I'm just wondering if anyone else is experiencing the same problem/issue/concern.

Just for reference, I'm running Ubuntu on an SLI system, running dual 7600GTs, using the latest nVidia graphics drivers (the ones suggested by Ubuntu when it told me that it needed to install drivers from the Restricted repository after I installed).  SLI is set to "Auto" in my xorg.conf.

The issue happens randomly, regardless of whether I am running an OpenGL application or not.

I wish I had a screenshot to share, because it's a hard thing to describe... I searched and searched for a similar problem before making this post, but couldn't come up with an adequate description to make the search fruitful.

Any help/insight that you can provide would be greatly appreciated!

---

### Post by kiwirobin on 2008-03-07
Played around with compiz settings and turning off **negative** under **Accessibility** got rid of it for me.

:)

---

