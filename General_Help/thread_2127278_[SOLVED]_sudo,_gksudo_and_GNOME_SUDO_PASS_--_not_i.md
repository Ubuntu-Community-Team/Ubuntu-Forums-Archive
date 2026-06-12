---
title: "[SOLVED] sudo, gksudo and GNOME_SUDO_PASS -- not in the man pages"
date: 2013-03-19
forum: General Help
---

### Post by questant on 2013-03-19
Checked to determine if the firewall was running:
$ ps aux | grep [g]ufw
root     27673  0.0  0.0 118100  4408 ?        Ss   Mar18   0:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- gufw
root     27678  0.0  0.0  12320  1448 ?        S    Mar18   0:00 /bin/bash /usr/bin/gufw
root     27679  1.4  4.2 2732256 251044 ?      Sl   Mar18  16:44 python /usr/lib/python2.7/dist-packages/gufw/gufw.py

A review of the first line reveals that all the sudo parameters listed are discussed in the man page except GNOME_SUDO_PASS.  Further search indicates it is likely either a return from sudo upon successful completion of password verification (read a lot of bug reports to ferret that out), or a "flag" that password input is necessary to proceed.  Can someone explain GNOME_SUDO_PASS use and why it is present in this line?

Thank you in advance for any light anyone can shed on this.

---

### Post by dino99 on 2013-03-19
Looks like a regression inside the libgksu2-0 package
if i'm not wrong, gnome_sudo_pass is one of its fonctions

you might raise a bug i suppose, explaining the steps to get that issue.

---

### Post by questant on 2013-03-19
Thank you for the response.   It indicates the analysis is in the right "zone."  The ufw gui (gufw) was initially started from the terminal with sudo (or, more likely, gksudo).  It then had to be "re-passworded" to unlock it for further configuration.  In a sense, that's two passwords for the (quasi) same operation.  That may have something to do with it.  Not sure but what the "bug" isn't "operator error."  Unless someone else recognizes an issue here.  It is interesting (may just show ignorance) ufw continues to run with the "g" on the front.  It was assumed the gui was a front end to the ufw back end and that ufw would run discretely from gufw, closing the gufw process when the gui was closed. I would consider this thread closed as well unless someone sees something of elevated significance that needs addressing.  Thank you once again for taking the time to reply.   :)

---

