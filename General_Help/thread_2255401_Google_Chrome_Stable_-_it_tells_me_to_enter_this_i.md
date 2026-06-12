---
title: "Google Chrome Stable - it tells me to enter this into terminal"
date: 2014-12-04
forum: General Help
---

### Post by michael-piziak on 2014-12-04
I'm using Ubuntu 12.04  lts

I downloaded the deb of Google Chrome.  I double clicked it and installed it.  It then said to type this into terminal:  google-chrome-stable

That' didn't work.  Do I need to put some sudo words before google-chrome-stable ?

See image.

---

### Post by deadflowr on 2014-12-04
You should have an icon for chrome in the dash now.
But to run from a terminal drop the stable part.
```
google-chrome
```

---

### Post by mc4man on 2014-12-04
As mentioned look for the launcher in the Dash
(- the  google-chrome command travels an interesting route - 
/usr/bin/google-chrome  > /etc/alternatives/google-chrome > /usr/bin/google-chrome-stable > /opt/google/chrome/google-chrome

 I gather to allow the install/use of the unstable version also.

---

