---
title: "missing X headers"
date: 2005-10-27
forum: General Help
---

### Post by kulashaker on 2005-10-27
Hi,

I'm trying to configure the Kdevelop source files, only I get an error from ./configure saying:

"Can't find X includes. Please check your installation and add the correct paths"

I have installed the libx11-dev package, but it didn't help. I'm wondering wich library contains the includes, the /usr/include/X11 og /usr/X11R6/include!?

How can I fix this?

Thank you in advance,
Kula

---

### Post by davmac on 2005-10-27
Have you installed the build-essential package?

HTH,

Dave Mac

---

### Post by stoeptegel on 2005-10-27
Most likely you're missing xlibs-dev.

---

### Post by kulashaker on 2005-10-27
hi,

I just installed both packages and the latter (xlibs-dev) had the desired effect -> problem solved!

Thank you! :cool:
Kula

---

