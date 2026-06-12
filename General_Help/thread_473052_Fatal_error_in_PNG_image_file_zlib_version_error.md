---
title: "Fatal error in PNG image file: zlib version error"
date: 2007-06-13
forum: General Help
---

### Post by jjgraveline on 2007-06-13
Yesterday I started to get the above message for the file /usr/share/gdm/themes/xubuntu/background.png and GDM would use a default theme.  Today I rebooted and now X won't even start.  I get the message:

could not open default font 'fixed'

I think the two issues could be related, but I'm not sure.  None of the standard fixes for not being able to find the default font 'fixed' seem to work.

Any help would be very much appreciated.

---

### Post by jjgraveline on 2007-06-14
It turns out that the two issues were indeed related. I had recently added some shared libraries to my ld.so.conf file.  When I removed them and ran ldconfig, everything went back to normal.

---

