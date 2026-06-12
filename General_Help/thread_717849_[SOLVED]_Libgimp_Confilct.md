---
title: "[SOLVED] Libgimp Confilct"
date: 2008-03-07
forum: General Help
---

### Post by Precipitous on 2008-03-07
I installed the Gimp 2.4.5 without first un-installing version 2.4.2. Now when I start the program I get the following msg. 

[COLOR="Blue"] Libgimp version mismatch!

The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.4.5, but the
libgimp version is 2.4.2.

Maybe you have GIMP versions in both /usr and /usr/local ?[/COLOR]

Version 2.4.5 is installed at /usr/local...  Any ideas as to the best way to handle this?

---

### Post by boeing777 on 2008-03-07
Completely remove GIMP from Synaptics.

Restart

Then install it again via Synaptic,

then it should workl

---

### Post by taurus on 2008-03-07
Can you go into synaptic and uninstall the older version and see if that fixes it?

---

### Post by Precipitous on 2008-03-07
When I select to un-install Gimp in Synaptic, Ubuntu-Desktop is being marked to be removed as well. I can't figure out how to remove Gimp, but leave Ubuntu-Desktop.

---

### Post by boeing777 on 2008-03-07
well, you can always reinstall the Ubuntu-Desktop

---

### Post by Precipitous on 2008-03-07
taurus/boeing777:

I completely uninstalled Gimp 2.4.2 via Synaptic, uninstalled version 2.4.5 via make uninstall, restarted computer, then re-installed version 2.4.2 via Synaptic. That did the trick. Thank You!!!!

---

