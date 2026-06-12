---
title: "ATI screen rotation problem"
date: 2007-05-05
forum: General Help
---

### Post by lotacus on 2007-05-05
I just bought myself a new 22" LCD monitor and looked up how to set rotation. The information I found seemed to only relate to tablet pc's and Nvidia drivers.

When I try to change it manually using xrandr I get the following output:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

I found a script for use with table pc's but seems to do the same thing as manually changing it through the console.

I have edited the xorg.conf file with the necessary option, but it still doesn't work.

Any solutions?

---

### Post by daeji on 2007-05-10
I have been trying to rotate my screen, just for fun and have had no luck.
At this moment in time I think it's safe to say the I can't find a solution.
The proprietary ATI drivers can't do a rotation.

---

