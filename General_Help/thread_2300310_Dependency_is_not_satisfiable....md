---
title: "Dependency is not satisfiable..."
date: 2015-10-24
forum: General Help
---

### Post by George W. Tush on 2015-10-24
***Dependency is not satisfiable: libgcrypt11 (>=1.4.5)***

I'm sure it is satisfiable... somehow.  But how?  

I just wiped out my hard drive tonight and did a fresh install of 15.10.  It is working without any problem, except that when I try to use the Software Center to install the Maxthon browser (which worked beautifully in 14.04), no installation happens.  I get the error message above.

If anyone can tell me how to correct this situation, I would be in your debt.

Thank you!

---

### Post by mc4man on 2015-10-25
There is no libgcrypt11 in 15.10 (libgcrypt20) & your app is built for/needs  libgcrypt11. So as is will not work. 
Best & likely only solution is to get the browser built for newer libgcrypt

---

