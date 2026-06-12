---
title: "Mosem Volume"
date: 2006-07-04
forum: General Help
---

### Post by cssutto on 2006-07-04
I would like to hear my modem dial.

I tried:

#

 $ sudo nano /etc/chatscripts/provider

#

Locate the line marked 'OK-AT-OK'.
#

Change 'ATDT' to 'ATxxDT', where 'xx' is one of the following:

    *

      M0 Silence the speaker
    *

      L1 Low volume
    *

      L2 Medium volume
    *

      L3 High volume

      For example: ATM0DT. Leave the rest of the line unchanged.

#

Save the file (Ctrl-o) and exit (Ctrl-x).


There is nothing in my /etc/chatscripts/provider
 and I don't know how to write one from scrath that will not screw up my system, which is running very well right now.

How?

CSSJR

---

