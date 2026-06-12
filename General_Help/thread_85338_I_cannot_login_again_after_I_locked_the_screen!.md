---
title: "I cannot login again after I locked the screen!"
date: 2005-11-02
forum: General Help
---

### Post by bsun on 2005-11-02
What happened then?  I found these lines in the log file.

Nov  2 09:36:25 xtao unix_chkpwd[8354]: check pass; user unknown
Nov  2 09:36:25 xtao xscreensaver[8226]: (pam_unix) authentication failure; 
logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=
 user=xtao
Nov  2 09:36:27 xtao unix_chkpwd[8355]: check pass; user unknown
Nov  2 09:36:27 xtao xscreensaver[8226]: (pam_unix) authentication failure; 
logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=
 user=root
Nov  2 09:36:30 xtao xscreensaver[8226]: FAILED LOGIN 2 ON DISPLAY ":0.0", FOR
 "xtao"

So I switched to root and then reboot because I can login with user name xtao from the start screen.

Anyone has any idea?

---

### Post by doc_holiday on 2005-11-02
keybord layout problem?

---

