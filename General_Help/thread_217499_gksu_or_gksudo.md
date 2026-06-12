---
title: "gksu or gksudo?"
date: 2006-07-17
forum: General Help
---

### Post by AirRaven on 2006-07-17
I've been using these two commands interchangably up until now as a replacement for standard [FONT="Courier New"]sudo[/FONT]. I'm wondering if there's any definite difference between the two functionality-wise.

Are there any drawbacks to using [FONT="Courier New"]gksu[/FONT] instead of [FONT="Courier New"]gksudo[/FONT]? The MAN page suggests that the former's a wrapper for [FONT="Courier New"]su[/FONT] while the latter's a wrapper for [FONT="Courier New"]sudo[/FONT], but both the former works fine without the root password enabled.

Which should I use?

---

### Post by aysiu on 2006-07-17
I've never had any problems with *gksudo*.

I would imagine they're interchangeable, but I have seen weird situations where something (like Synaptic) did not work with *gksu* but did work with *gksudo*.

That's odd, of course, because I believe the default command for Synaptic is ```
gksu synaptic
```

---

### Post by eeried on 2006-10-06
It'd be nice if the doc answered this question.

Can we take for granted gksudo works in all cases?

Actually I've only just realized that gksudo existed -- it doesn't make things simpler for newbies wanting to learn how to use the command line (which I enjoy). Is this a Gnome thing?

---

