---
title: "&quot;packard bell dot-s&quot; problem with display brightness (too dark)"
date: 2013-03-19
forum: General Help
---

### Post by daviebasite on 2013-03-19
Hi there,
I tried ubuntu 12.04 live usb and it was working very well then Idecided to install it on the internal hdd and here also everything went fine.After I boot from the all ready new installed ubuntu the desktop looks very dark and the brightness controls are not working.

I'm wondering how the live one works without a problem but the installed one looks like something with the display drivers is broken?

I all ready tried some of the solutions from the forum but without a success.
1. `**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"**`
2. echo 4 > /sys/class/backlight/acpi_video0/brightness

I'll appreciate any help and thoughts about this problem. Thanks!

EDIT:
this solution worked for me, the buttons stil doesn't work but at least the display is bright again. Still appreciating any thoughts about how to make the brightness buttons back in business.
Thanks!
[http://www.cebuntu.com/how-to/how-set-brightness-on-startup-ubuntu-12-04/](http://www.cebuntu.com/how-to/how-set-brightness-on-startup-ubuntu-12-04/)

---

### Post by cuptos on 2013-04-14
I don't know if it is too late to post on this thread, but here I go.
I have the same netbook and the solution provided in this thread [http://ubuntuforums.org/showthread.php?t=2135036](http://ubuntuforums.org/showthread.php?t=2135036) worked like a charm.
Good luck

---

