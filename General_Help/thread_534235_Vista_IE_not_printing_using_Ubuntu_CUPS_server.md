---
title: "Vista IE not printing using Ubuntu CUPS server"
date: 2007-08-25
forum: General Help
---

### Post by rkadir on 2007-08-25
I have setup a CUPS server on Ubuntu.  I have 2 vista PC's and 1 XP PC.  Printing from all applications except IE 7 on Vista works. On XP , IE prints perfectly fine. I have checked the /var/log/cups/error_log and found  nothing while trying to print on Vista.  How could I get IE on Vista to print.  It's just fustrating because all other applications print without a problem

---

### Post by yaztromo on 2008-01-08
I found turning protected mode off in the IE7 security options fixed this. It's not a bug with ubuntu, it's a UAC bug in vista.

Best workaround is to install firefox on the vista machines and leave UAC turned on for highest security.

---

