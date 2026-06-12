---
title: "howto setup user's startup script ?"
date: 2004-10-31
forum: General Help
---

### Post by dunric on 2004-10-31
I'd like to run custom user script after gdm login. For console interactive login it's shell startup file like ~/.bash_profile. But for gdm ?

Thx in advance

---

### Post by ynef on 2004-10-31
[QUOTE=dunric]I'd like to run custom user script after gdm login. For console interactive login it's shell startup file like ~/.bash_profile. But for gdm ?

Thx in advance[/QUOTE]
 .xsession

Don't forget to add "gnome-session" to the end of it though! Search the forums, I wrote a more detailed post earlier.

---

### Post by Joshua Swink on 2007-07-13
> **ynef said:**
> .xsession

Don't forget to add "gnome-session" to the end of it though! Search the forums, I wrote a more detailed post earlier.

This only works if you choose "Run Xclient script" for your session. Is there a script that gdm will run no matter what session you choose?

---

