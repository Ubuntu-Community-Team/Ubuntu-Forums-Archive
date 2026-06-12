---
title: "Gutsy: Regenerating fonts cache failed"
date: 2007-11-05
forum: General Help
---

### Post by desheikh on 2007-11-05
Hi,

When I do 
sudo dpkg-reconfigure fontconfig in gutsy
I get the error
Regenerating fonts cache.. failed

and in /var/log/fontconfig.log

/usr/share/fonts: /usr/share/fonts: failed to write cache
caching, 0 fonts, 3 dirs
/usr/share/fonts/X11: /usr/share/fonts/X11: failed to write cache
caching, 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: /usr/share/fonts/X11/100dpi: failed to write cache
caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: /usr/share/fonts/X11/75dpi: failed to write cache
caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: /usr/share/fonts/X11/Type1: failed to write cache
caching, 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: /usr/share/fonts/X11/encodings: failed to write cache
caching, 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: /usr/share/fonts/X11/encodings/large: failed to write cache
caching, 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: /usr/share/fonts/X11/misc: failed to write cache
caching, 0 fonts, 0 dirs

.............

/var/lib/defoma/fontconfig.d/m: caching, 2 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: caching, 1 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
fc-cache: failed

I installed the msttcorefonts before trying this and they arent apearing in openoffice either...

Any idea what the issue is?
Thanks.
Ali

---

### Post by desheikh on 2007-11-05
Just did an update and it seems to have fixed the problem.

---

