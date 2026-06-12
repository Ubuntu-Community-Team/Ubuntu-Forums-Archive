---
title: "acroread fails with LDAP/getpwuid"
date: 2007-07-19
forum: General Help
---

### Post by gauss on 2007-07-19
I have Feisty Fawn/AMD64 and installed acroread from Medibuntu. I login with LDAP authentication since I'm in a college environment. My local, non-LDAP users can use acroread but I (and any other LDAP-authenticated user) cannot.

My error messages:
```
(acroread:19155): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (1234)

(acroread:19155): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",

(acroread:19155): Gtk-WARNING **: Unable to locate theme engine in module_path: "qtengine",
```
I think the first error relates to LDAP and am not sure about the other two. Does anyone have any idea what to do?

Thanks.

---

