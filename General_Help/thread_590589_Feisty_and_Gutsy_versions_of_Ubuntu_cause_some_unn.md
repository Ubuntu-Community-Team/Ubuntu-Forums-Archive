---
title: "Feisty and Gutsy versions of Ubuntu cause some unnecessary wear and tear on a hard dr"
date: 2007-10-24
forum: General Help
---

### Post by nacho32 on 2007-10-24
is this true I found this article off Digg.com that takes you to this [site]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")
if so is their a patch or fix on the way ? or is it All just BS?

---

### Post by bytor4232 on 2007-10-25
Mostly BS.  To know if your effected by this, run:

sudo hdparm -i /dev/sda | grep AdvancedPM

If you get back:   **AdvancedPM=no WriteCache=enabled**
Then your not effected.  I checked two desktops that I have access to here, and neither of them are effected.  Its probably a laptop issue, or a non-issue period.  You want your hard drive to spin down when using a laptop, it saves while on battery.

---

