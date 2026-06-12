---
title: "gnome-system-log log viewer does not show times"
date: 2015-07-06
forum: General Help
---

### Post by sam_baker2 on 2015-07-06
Hi,
I just installed 14.04 xubuntu, and when I open gnome-system-log ( version 3.8.1 ),
there are no times given. 
It worked ok in 12.04

Any ideas appreciated

---

### Post by Dennis N on 2015-07-06
In the default view, the font color for the date and time (at start of each line) is the same as the background color, so you can't see it. If you use a filter with user specified text (highlight > foreground) color (like black!), it will be visible in the filtered results.

_Workaround:_
If you don't want to create or use a filter, an easy way to see the date and time is to use CTRL+A to select all - this makes the date and time visible as well. Optionally, you could then copy the entire output to the text editor to view.

---

### Post by sam_baker2 on 2015-07-07
Thanks Dennis N  I tried that and got that to work. I found another log viewer, ksystemlog, which I believe is actually for KDE, but it works ok and it has a lot of neat options on it.

---

