---
title: "restore default font configuration from mac4lin"
date: 2007-12-04
forum: General Help
---

### Post by basibanget on 2007-12-04
I installed the font configuration from mac4lin and now I want to restore the default font configuration of Gutsy. anyone knows how to do this?

---

### Post by ariek on 2007-12-04
Hi,

If mean  the font settings, in stead  of the fonts, then:
cd /etc/fonts
remove all **but**
conf.avail  conf.d  fonts.conf  fonts.dtd
and logoff/logon.

---

