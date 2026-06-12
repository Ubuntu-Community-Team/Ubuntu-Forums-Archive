---
title: "Applications in gnome-terminal freeze when Terminal window loses focus"
date: 2012-10-20
forum: General Help
---

### Post by james_mcl on 2012-10-20
I've got some applications which run in the terminal, and which I was hoping to leave running while I got on with some work. However, as soon as I move to a new window, System Monitor shows a drop in activity, and when I return to the gnome-terminal window it turns out to be because the application has frozen.

Clicking on the Terminal window gets the application going again - until focus moves away again.

I'm not sure what the cause of this problem is, or even if I'm posting in the right place. I can state the following for certain:

1.) This is a problem which didn't occur under GNOME 2 on Ubuntu Natty.

2.) It does occur when using MATE in Ubuntu Precise.

3.) Both mate-terminal and gnome-terminal are affected.

4.) LXTerminal is NOT affected - so I do have a workaround for the problem; use LXTerminal instead. But I would like to get gnome-terminal and mate-terminal to behave properly as well.

5.) I tried compiling these applications with g++ 4.5 as well as 4.6. It didn't make a difference; the problem persisted whichever version I used.

I've googled quite a bit for information on this problem, but haven't found anything.

James McLaughlin.

---

### Post by james_mcl on 2012-11-03
Partly a bump - surely *someone* else must have encountered this issue?

But also just to note that xfce4-terminal isn't affected by the problem, and since LXTerminal doesn't have the "Select All" option in the Edit menu that the other terminal emulators have, using xfce4-terminal is probably a better choice of workaround.

(Only discovered that today!)

---

