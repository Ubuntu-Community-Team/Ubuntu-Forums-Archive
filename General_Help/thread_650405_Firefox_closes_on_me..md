---
title: "Firefox closes on me."
date: 2007-12-26
forum: General Help
---

### Post by chm0d on 2007-12-26
Hey guys!

    I was just using firefox trying to get directions for my families camping trip next week, and I use yahoo maps.  I haven't tried anywheres else yet.  Anyway, when I put both addresses in and click go for the directions firefox closes on me and I get this error:

firefox-bin: /build/buildd/libcairo-1.4.10/src/cairo-pen.c:325: _cairo_pen_find_active_cw_vertex_index: Assertion `i < pen->num_vertices' failed.
Aborted (core dumped)

I have googled and didn't really find anything.  LIbcairo is installed on my computer.  Anyone have any ideas on this?  TIA

Rich

---

### Post by LaRoza on 2007-12-26
What version of Firefox is this?

---

### Post by agurk on 2007-12-26
Confirmed bug [https://bugs.launchpad.net/libcairo/+bug/124547](https://bugs.launchpad.net/libcairo/+bug/124547) but seemingly no activity.
There's a hack posted at [http://lists.cairographics.org/archives/cairo/2007-August/011283.html](http://lists.cairographics.org/archives/cairo/2007-August/011283.html) but I don't know if it has found its way into the cairo repository or not.

[https://bugs.freedesktop.org/show_bug.cgi?id=11493](https://bugs.freedesktop.org/show_bug.cgi?id=11493) is still repeatable on my machine as well.

---

### Post by chm0d on 2007-12-26
thank you for the reply.  I guess all we can do now is wait for an update :)

Rich

---

### Post by agurk on 2007-12-26
No problem. You could always check with the Hardy Heron testers if they can repeat the problem, it's a simple and quick testcase. I see that the current Hardy version of libcairo is 1.5.4. Alternatively, I think you could grab a Hardy alpha version live CD and find out yourself, evince should be in there.
If the bug is still present, I think we should make sure that it has been filed in the right bugtracker. For all we know, the libcairo developers could be completely unaware of this crash bug.

---

### Post by NT4usB on 2008-01-20
Ain't it always the way it goes... I built a half dozen boxes, playing with and learning Ubuntu. Never had a problem with Firefox and Yahoo Maps.
First box I build for someone else (mom) and Yahoo Maps crashes Firefox.
A couple hours of googling finds sporadic reports and no obvious solutions...
Going over tonight to try and fix it.

---

