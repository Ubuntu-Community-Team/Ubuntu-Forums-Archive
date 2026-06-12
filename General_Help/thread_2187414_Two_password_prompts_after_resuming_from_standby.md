---
title: "Two password prompts after resuming from standby"
date: 2013-11-12
forum: General Help
---

### Post by bovender on 2013-11-12
Since upgrading from 13.04 to 13.10, I need to enter the password twice when resuming from standby. The first password prompt is the typical Ubuntu Unity one. When I enter the password, the desktop is shown briefly (about 1 second or so), then the screen turns dark again and shows me the Gnome 3 password prompt. When I enter the password there, I can continue to work with the machine.

How do I turn off the superfluous Gnome password prompt?

---

### Post by cong06 on 2014-01-01
I had this problem after I did a clean install of 12.04 -> 13.10 (bringing my old home directory over).

I somehow managed to fix it by uninstalling and reinstalling gnome-screensaver, and toggling the settings in "brightness & lock"

---

### Post by bovender on 2014-01-05
Hm, this didn't do it for me...

---

### Post by bela83 on 2014-03-29
I encounter the same problem...
Is there a solution ?

---

### Post by texaswriter on 2014-04-05
*BUMP*

Yes, this is still a problem. Does someone know if there is a bug report filed already?

---

### Post by kid1000002000 on 2014-07-12
Here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1296270](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1296270)

---

### Post by bapoumba on 2014-07-12
Marked as affecting me too.

---

