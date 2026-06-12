---
title: "Remote access"
date: 2012-12-06
forum: General Help
---

### Post by paramub on 2012-12-06
Hi,

How can i take Remote Access of my Ubuntu System, so that the screen get locked on other side. 
for eg:- if i take RDP of Window XP, from another system than the Console session or Original System display get locked.

I hope you understood my question.

Thanks & Regards,
Param

---

### Post by SeijiSensei on 2012-12-06
Since Linux, like all Unix derivatives, is inherently multi-user, I doubt this is possible.  Also most of us who manage systems remotely do so in text-mode via SSH.  In that situation there is no "remote desktop" to lock down.

Maybe one of the remote access clients like NX or VNC allow this, but it would only apply to your session.  There's nothing to stop someone logging in from the keyboard and starting another session in parallel with yours.

---

### Post by rnerwein on 2012-12-06
> **SeijiSensei said:**
> Since Linux, like all Unix derivatives, is inherently multi-user, I doubt this is possible.  Also most of us who manage systems remotely do so in text-mode via SSH.  In that situation there is no "remote desktop" to lock down.

Maybe one of the remote access clients like NX or VNC allow this, but it would only apply to your session.  There's nothing to stop someone logging in from the keyboard and starting another session in parallel with yours.
you can (without root) anticipate the login from normal users via "pam_nologin". 
--> man pam_login

cheers

---

