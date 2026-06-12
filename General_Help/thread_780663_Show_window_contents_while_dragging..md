---
title: "Show window contents while dragging."
date: 2008-05-03
forum: General Help
---

### Post by jastonas on 2008-05-03
Hi guys, need some help again! I ve got Hardy 8.04 and while resizing I cant see the contents of the window. How can I change this?

---

### Post by SomeGuyDude on 2008-05-03
I -believe- there's a Compiz plugin that does this, but I'm on my way to work so I can't look it up at the moment. It can be done, I had it for a while.

All I will say, though, is that it wasn't smooth at all. Kinda herky jerky.

---

### Post by jastonas on 2008-05-03
Strange for compiz which is an amazing decorator not to have that a simple thing!

---

### Post by Zorael on 2008-05-04
Huh.

Pop up ccsm (compizconfig-settings-manager package), make sure the Resize Window plugin is enabled, go into its preferences and change default mode to normal. Presto.

---

### Post by jastonas on 2008-05-04
Yes that is enabled!

---

### Post by jastonas on 2008-05-06
strangely.. its very slow when you enable the normal mode...

---

### Post by CrazyGuy123 on 2008-05-06
I think it's a bit of an archetecture problem - compiz needs to allocate a new buffer, copy from one to the other, and request the window redraw itself every time the mouse is moved while resizing.

I agree it does feel like going back to the old Windows 95 days though...

---

### Post by jastonas on 2008-05-06
haha! True!
Lets hope it gets fixed soon :)

---

### Post by tdr2009 on 2010-08-19
Sorry if im bumping, if thats what you call it, but there is a way that looks better than normal. instead of clicking Normal in the window resize options, click stretch. Its much smoother.

---

