---
title: "Battery drain very fast"
date: 2020-02-09
forum: General Help
---

### Post by handuup on 2020-02-09
Hi guys. I'm new to Ubuntu but I'm having some problems with the battery: it drains really fast. I installed ```
powertop
``` and it gives me this (see attached files). Also, the Software And Update App gives me a problem with wifi drivers, even I have no connection problems. Finally, this command: ```
lspci | grep -E 'VGA|Display|3D'
``` gives me output:```
 00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R3 Graphics] (rev 40)

```

---

### Post by letmeknow on 2020-02-09
Not sure if it helps: Do you boot in secure mode? Some drivers can be installed only in (if I remember right) not secure mode because they are not signed.

I have a simular (or better 2) issues.

I hope it is not inpolite to add a question too. I do have also trouble, my core-m5 system (ubuntu 18.04) drains to much power.
I identified two potential problems: 
a) The processor's GPU seems not to use power save states rc6 and below - but according to ... it seems to be enabled?!?
sudo cat devices/pci0000:00/0000:00:02.0/drm/card0/power/rc6_enable
 1

b) Also my wifi driver consumes a lot of power (according to powertop), even withoutl almost no traffic. Maybe it doesn't support power saving mechanism.
See also the report of additional driver output...

Maybe one additonal question: How can I check the processor states while it is in standby - so whether is uses deepest available mechnism C9/C10 ?
Thank you.

---

