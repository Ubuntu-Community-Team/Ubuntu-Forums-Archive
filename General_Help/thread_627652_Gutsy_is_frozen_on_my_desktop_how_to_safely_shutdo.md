---
title: "Gutsy is frozen on my desktop: how to safely shutdown?"
date: 2007-11-30
forum: General Help
---

### Post by xi'an on 2007-11-30
Gustsy has frozen on my desktop.  I remember reading that there was a  combination of keys that permits a safe shutdown to recover from this.  

Can someone tell me what to do?

Thanks!

---

### Post by geirha on 2007-11-30
Is it Xorg that has frozen? You can kill xorg by hitting CTRL+ALT+Backspace, which should return you to the login-screen.

---

### Post by Emerzen on 2007-11-30
If that doesn't work try:

CTRL+ALT+F1

login at the prompt

type "sudo init 6" (without the quotes) enter password and it will reboot

---

### Post by xi'an on 2007-11-30
Thanks.  I tried both suggestions, but there was no response.  Still frozen.  Unfortunately I do not know what in particular is frozen, just that there is no response: can't move the mouse, and don't know what else to do.

---

### Post by PmDematagoda on 2007-11-30
May be this [thread]("http://ubuntuforums.org/showthread.php?t=617349") could help you.

---

