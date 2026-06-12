---
title: "[SOLVED] flash video using unreasonable amounts of processing power"
date: 2008-05-27
forum: General Help
---

### Post by werries on 2008-05-27
Ok so upon watching youtube today while watching the system monitor i noticed that it was staying at around 90%-100% when running flash videos. Checked on other sites also.

However, video on the pc itself, like a .avi played in vlc, does not bring it up to this level. This worries me only because it brings my computer up about 10 degrees when playing and uses up power from other things.

Is this high amount of processing normal?

If it matters, i have an nvidia geforce 7400, using nvidia-glx-new. And i got the new kernel 2.6.24-17 today. dunno if that makes a difference

---

### Post by sdennie on 2008-05-27
Yes, it's normal.  Adobe Flash is horrible on the CPU (pretty light on the GPU though...) on linux.  Nothing can really be done about it until a viable Adobe Flash alternative is available (gnash is getting there but, not quite there).

Note: Depending on the size of your gnome-system-monitor window, you may be exasperating the problem simply by having the monitor up.  See the sticky post at the top of this sub-forum.

---

### Post by jrusso2 on 2008-05-27
Adobe flash uses a lot of CPU but not 100 % unless you have a really old and slow CPU

---

### Post by werries on 2008-05-27
not 100% constantly, but it spikes up there.
and the system monitor is just the little icon you can put on the gnome taskbar at the top. is this consuming power too?

---

### Post by sdennie on 2008-05-27
No, the applet doesn't use a noticeable amount of CPU.  It's double clicking it and bringing up the more detailed display that uses large amounts of CPU (when the window is large, specifically maximized (though, I haven't updated this week so maybe it's fixed (it's been gradually getting better)).  Flash isn't multi-threaded so, based on the fact that you are talking about ~100% of the CPU, I'm going to assuming you are using an older processor because on multi-core systems, it just uses a single core.  This behavior is unfortunate but normal.

---

### Post by madelaki on 2008-05-27
Don't worry, it is normal. Not saying it isn't annoying though. As vor said, Gnash is getting there, be patient. 

> and the system monitor is just the little icon you can put on the gnome taskbar at the top. is this consuming power too?

It shouldn't.

---

### Post by werries on 2008-05-27
alright thanks. and no no, the icon puts the two processors together. plus i think i was doing other stuff. it just worried me.

---

