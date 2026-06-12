---
title: "Trying to use USB-Serial cable"
date: 2015-08-04
forum: General Help
---

### Post by Sheldon_Livingston on 2015-08-04
I've installed Ubuntu 14 on my machine and I wish to administer a FireBox unit.

If I attach my USB to Serial cable and run DMESG I see the cable attached to ttyUSB0.

If I run:

screen /dev/ttyUSB0 9600

The term screen blanks and I see [screen is terminating].  This is whether the serial end is attached to the FireBox or not.

Leaving off the 0 after ttyUSB shows a "no such file or directory" error.

Any thoughts?

---

### Post by TheFu on 2015-08-05
I've never used screen for this - always used minicom.

---

### Post by Lars Noodén on 2015-08-05
I don't use screen for that either, I tend to use [cu](http://manpages.ubuntu.com/manpages/trusty/en/man1/cu.1.html), so I am not familiar with screen's errors or lack thereof.  

However, I suspect that you might not be in the group 'dialout'  Look at /dev/ttyUSB0 with 'ls -l' to see which group it is in.  It is probably 'dailout' add yourself to that group and log back in again and it should work.

---

