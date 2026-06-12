---
title: "Thunderbird corrupted"
date: 2015-09-21
forum: General Help
---

### Post by tornadof3 on 2015-09-21
So,

Launching Thunderbird on my machine fails (before upgrade to 15.04, it worked fine....). If I launch from the command line, I get these errors:

```
~$ thunderbird

(process:3622): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(thunderbird:3622): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (10000)
enigmail.js: Registered components
mimeVerify.jsm: module initialized

```

This machine uses LDAP (successfully) for user auth and no other program has a problem. Interestingly, clicking a mailto: link works in that it opens a new mail message window and that seems ok- it's the 'main' program that won't load. Any ideas? 
Also, user id 10,000 is me in LDAP and works fine from the terminal when I run the ```
id
``` command

---

