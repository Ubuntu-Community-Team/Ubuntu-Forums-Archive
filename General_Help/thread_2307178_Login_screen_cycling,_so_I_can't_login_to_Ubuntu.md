---
title: "Login screen cycling, so I can't login to Ubuntu"
date: 2015-12-22
forum: General Help
---

### Post by t0p on 2015-12-22
Trying to login, it recycles to login.  I tried ```
rm .Xauthority
```and rebooting, but problem remained.  I tried 'df -h' to see if space was the problem and got this:```
df: '/run/user/112/gvfs': Permission denied
```followed by normal usage output.The 'Permission denied' at the start of the 'df -h' output seems to mean to me that permissions have got screwed somehow.  Don't know how though.  This is a fresh install.Ubuntu 12.04.3.

---

