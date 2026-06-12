---
title: "Fixed Fonts and 6x13 in Edgy"
date: 2007-01-15
forum: General Help
---

### Post by wildutah on 2007-01-15
Lots of people miss the 6x13 fixed font and other bitmapped fonts in Ubuntu Edgy.  It used to be you could dpkg-reconfigure fontconfig and reenable your bitmapped fonts but that won't work anymore.

Yes, the fontconfig people have really been working hard to deny you your bitmapped fonts.  They think those fonts are ugly and you aren't smart enough to use them.

Try copying the /etc/fonts/conf.d/yes-bitmaps.conf file to your local directory  and rename it ~/.fonts.conf

That might work.

---

