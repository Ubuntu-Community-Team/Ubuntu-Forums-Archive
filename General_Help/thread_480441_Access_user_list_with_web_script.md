---
title: "Access user list with web script?"
date: 2007-06-21
forum: General Help
---

### Post by Airjoe on 2007-06-21
Hey,
I'm working on a web site for someone, and for the login page for administration, I'd like it to tie in directly to Linux's own user/password system. Is this at all possible? How would I go about doing this? 

Thanks!

---

### Post by TacticalPenguin on 2007-06-21
I HIGHLY doubt that's possible, there's no way you'd ever get a linux user's password from a web app.

---

### Post by shizeon on 2007-06-21
Hi Airjoe.  If you are using apache, then yes it is totally possible.  Google for mod_auth_pam.  It is an apache module that can tie in to the base authentication system.   Might not be the best from a security standpoint unless you are using SSL and strong passwords, but should work.  It is in the repos under the name 'libapache2-mod-auth-pam" and 'libapache-mod-auth-pam" depending on apache 1 or 2.

---

### Post by Daveski on 2007-10-11
I can't seem to get either PAM (to unix passwords) or MySQL authentication working in Apache on Feisty. Has anyone managed Basic authentication without having the username / password in the .htaccess files?

---

