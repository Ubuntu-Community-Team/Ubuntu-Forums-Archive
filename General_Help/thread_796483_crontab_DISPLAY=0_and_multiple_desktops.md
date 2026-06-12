---
title: "crontab DISPLAY=:0 and multiple desktops"
date: 2008-05-16
forum: General Help
---

### Post by mailbox on 2008-05-16
I'm using XFCE with 64 bit 8.04, and I have this script:
**0,20,40 * * * *    DISPLAY=:0 /usr/bin/xfdesktop -reload  >/dev/null 2>&1**
in my crontab to give me a random desktop background every 20 minutes. I was wondering if it was possible to somehow add a line or command in there somewhere to give me a different background for *each* desktop every 20 minutes.
Thanks in advance.

---

### Post by mailbox on 2008-05-16
Bump.
Anyone?

---

### Post by Tec5nical on 2009-09-10
Cannot U use these codes? :
0,20,40 * * * * DISPLAY=:0 /usr/bin/xfdesktop -reload >/dev/null 2>&1
0,20,40 * * * * DISPLAY=:1 /usr/bin/xfdesktop -reload >/dev/null 2>&1
etc.

---

