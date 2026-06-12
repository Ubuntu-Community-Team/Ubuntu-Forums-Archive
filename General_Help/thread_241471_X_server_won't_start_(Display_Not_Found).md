---
title: "X server won't start (Display Not Found)"
date: 2006-08-22
forum: General Help
---

### Post by Donnut on 2006-08-22
Hi all.  I just tried to install the radion drivers, and now my xserver will not boot.  I have tried reconfiguring the xserver several times, with different drivers, tried removing and installing the xserver-xorg, ubuntu-desktop, linux-restricted modules, and everything with no avail.  When I go into recovery mode and try startx, it gives me a "display not found" error, and from what I could find out, I have to set the display on 1 instead of 0.  But I cannot Xorg.conf to do this, not even in root.  The sudo dpkg-reconfigure xserver-xorg gives me PCI:1:0:0.  Is there anything I can change about this?  I do not want to reformat m HD again...

---

### Post by taurus on 2006-08-22
At the prompt, run

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Donnut on 2006-08-22
I did that, it still says display not found...

---

### Post by mostwanted on 2006-08-22
You sure this isn't caused by the recent buggy update to the xserver-xorg-core package? See the notice in green on the front page.

---

### Post by taurus on 2006-08-22
Maybe you want to look in /etc/X11/xorg.conf to make sure there is a section for your Monitor...

```

more /etc/X11/xorg.conf <-- to view it
sudo nano /etc/X11/xorg.conf <-- to edit it from a terminal

```

---

### Post by Donnut on 2006-08-22
Thank you all for your quick replies to my problem.  I'm an idiot and did not read the front, when an update came along I just hit download and installed it.  After I backdated it all was restored.

---

