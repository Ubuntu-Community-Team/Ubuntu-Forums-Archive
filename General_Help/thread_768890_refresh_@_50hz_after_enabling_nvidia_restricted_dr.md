---
title: "refresh @ 50hz after enabling nvidia restricted drivers"
date: 2008-04-26
forum: General Help
---

### Post by bishop9226 on 2008-04-26
i just installed hardy, was happy at my nice 60hz.  then i enabled the latest nvidia drivers and bam, down to 50hz!

using nvidia 7300go 
dell e1505 core 2 duo

---

### Post by Linja on 2008-04-26
Put this:

Option          "DynamicTwinView" "False"

under the "Screen" heading in your /etc/X11/xorg.conf file, right beneath the "Monitor" line. Nvidia bug.

---

