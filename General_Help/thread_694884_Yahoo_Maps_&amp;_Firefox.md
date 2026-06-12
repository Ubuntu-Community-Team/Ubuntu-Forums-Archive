---
title: "Yahoo Maps &amp; Firefox"
date: 2008-02-12
forum: General Help
---

### Post by Het Irv on 2008-02-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/180728](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/180728) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Has anyone seen a fix for this?
I can search for one address no problem, it is when I try two addresses that it crashes.

The terminal gives me this error:
```
firefox-bin: /build/buildd/libcairo-1.4.10/src/cairo-pen.c:325: _cairo_pen_find_active_cw_vertex_index: Assertion `i < pen->num_vertices' failed.
```

The most obivous work around would be to use Google, but I prefer Yahoo. Any Ideas?

---

### Post by apetresc on 2008-02-12
Judging by the bug report this is an undiagnosed, unsolved problem. I'll take a look tonight after work and see if I can figure anything out.

I've subscribed to the bug and I'll post back here if I learn anything tonight.

---

### Post by Het Irv on 2008-02-12
That is how the Bug Report looked to me, but it also seemed like it was forgotten.

---

### Post by pressman57 on 2008-03-02
I've seen the bug report and appended my two-cents worth but thought it may be worth a shot to post to this thread in hopes of finding a solution.

I've got Gentoo installed on another hard-disk (firefox 2.0.0.9 with flash 9.0.115.0) and the problem doesn't exist. It seems to me that this bug is either distribution-specific or  occurs as a result of the type of flash player (non-free)  in ubuntu.

Firefox and flash were just upgraded by apt but the problem persists. Any thoughts?

---

### Post by sancho panza on 2008-03-02
I too am very much annoyed by this issue. I prefer yahoo maps over google. Sorry I cannot do much research on this issue. As far as I know, I have not made any changes in firefox or flashplayer from the default ubuntu config except for the regular system updates.

---

