---
title: "Drop Shadows, transparency without moving to X.org"
date: 2004-10-15
forum: General Help
---

### Post by oddabe19 on 2004-10-15
Can someone do a How To on drop shadows and transparencies without moving to X.org? I tried moving to X.org (CVS) on my Debian Sid system, and it fried it.... So i'm scared to do it in Ubuntu.
I don't have the Knowledge to do a FAQ on something like this.

Thanks.

---

### Post by iwasbiggs on 2004-10-17
You can't, unless you get the new XFree installed or the X.org installed. The translucent menus and shadows are associated with the composite extension and that extension is only available in newer versions of the x servers.

There was a hack for gtk+ menu shadows (only) from the xfce developers that doesn't require the new versions of x servers. Google for it.

---

