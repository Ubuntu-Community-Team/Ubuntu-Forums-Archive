---
title: "Burn a dvd iso from the command line"
date: 2006-12-31
forum: General Help
---

### Post by bruenig on 2006-12-31
I have an iso located at ~/dvd.iso and I am trying to burn it to a blank dvd in /dev/hdc in the command line, anybody know how?

---

### Post by snowx1000 on 2006-12-31
This should do the trick:

growisofs -dvd-compat -Z /dev/hdc=dvd.iso

---

### Post by bruenig on 2006-12-31
Works perfect, thanks.

---

### Post by mtierney on 2007-01-29
I found that I needed to use the following command:

growisofs -dvd-compat -Z /dev/dvd=dvd.iso

Just a slight variation :-)

---

