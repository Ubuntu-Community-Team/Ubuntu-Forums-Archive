---
title: "Apache2 - Completely remove it?"
date: 2007-04-06
forum: General Help
---

### Post by ~LoKe on 2007-04-06
I'm trying to remove everything relating to apache2 (including everything in /etc/apache2).  I'm having problems with it from something I tried to do, and I'd like to start with a clean slate.

So...what's the best way to remove apache2 and all the configuration files?

[dpkg -r apache2 doesn't remove everything]

**EDIT:** Unless, of course, someone thinks they can help me fix this problem.  I'm getting this error when I try to start Apache:
>  * Forcing reload of web server (apache2)...                                    [Fri Apr 06 19:40:20 2007] [warn] module authn_file_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module authz_host_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module authz_groupfile_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module authz_user_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module authz_default_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module auth_basic_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module env_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module setenvif_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module mime_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module status_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module autoindex_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module cgid_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module negotiation_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module dir_module is already loaded, skipping
[Fri Apr 06 19:40:20 2007] [warn] module alias_module is already loaded, skipping
httpd (no pid file) not running
[Fri Apr 06 19:40:30 2007] [warn] module authn_file_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module authz_host_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module authz_groupfile_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module authz_user_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module authz_default_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module auth_basic_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module env_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module setenvif_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module mime_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module status_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module autoindex_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module cgid_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module negotiation_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module dir_module is already loaded, skipping
[Fri Apr 06 19:40:30 2007] [warn] module alias_module is already loaded, skipping
( 98 )Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by ~LoKe on 2007-04-06
Bump.

---

### Post by ~LoKe on 2007-04-07
One more?

---

### Post by hikaricore on 2007-04-07
have you tried:

```
sudo apt-get --purge remove apache2
```

This should stop apache then completely remove it and all it's configuration files.

Note if you have added files inside the /etc/apache2 directory, it will not be completely removed.

---

### Post by ~LoKe on 2007-04-07
**EDIT:** Got it!  I had to purge apache2.2-common, as well.  Thanks!

---

