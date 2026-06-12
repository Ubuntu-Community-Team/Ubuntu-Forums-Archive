---
title: "Ubuntu Edgy becomes very slow yesterday"
date: 2006-10-24
forum: General Help
---

### Post by 3str on 2006-10-24
Hi, I've been using edgy since RC1. My problem happened yesterday. When the X window is up and the gnome splash appears, the system gets slow suddenly. After that, the gnome panel doesn't function properly, I can't start anything from it.

Can anyone help?

---

### Post by 3str on 2006-10-24
I found that during the gnome splash time, java took about 90% of the CPU time, but how can java get involved?

Here is a boot chart, thx.

---

### Post by barney_1 on 2006-11-04
I just started having the same problem.  My gnome-panel will work, but sometimes I have to wait 40 seconds for it to respond to a click.  It is very slow loading after login, maybe taking 1 minutes to appear fully rendered.  Any idea the problem?

I just did an update,  I know it included linux-restricted-modules-common, if that matters.

---

### Post by barney_1 on 2006-11-09
I believe I have fixed my problem.  It seems to have been a corrupted swap partition caused by the upgrade to edgy.  Check out [this post]("http://www.ubuntuforums.org/showthread.php?t=287096&highlight=swap+signature") for help.

---

### Post by 3str on 2006-11-09
You mean after an upgrade, your swap is not mounted?
I didn't upgrade. I used a fresh install...
But now I reinstalled with the final release of edgy. It seems to be running nicely:-)

---

### Post by barney_1 on 2006-11-09
I was getting an error along the lines of: Unable to find swap signature.

Seems my swap partition was corrupt.  That's as much as I could figure out anyway, and I no longer have the problem.

---

