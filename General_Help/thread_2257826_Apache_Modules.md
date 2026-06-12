---
title: "Apache Modules"
date: 2014-12-22
forum: General Help
---

### Post by cobras on 2014-12-22
I've been trying to speed up my website by implementing some cache control.  By the way I'm running Ubuntu 12.04 and my server's Apache version is Apache/2.2.27 (Unix).                                                                         

My skills at the command line are VERY basic, and I just began to browse through Apache's documentation.  At this point I've been able to access the SSH shell but when I go to check what modules are enabled with 'apachectl -M' I get 

"httpd: Could not open configuration file /etc/httpd/conf/httpd.conf: No such file or directory".  I believe my shared server does not grant me access to httpd.conf.  I need to go through the .htaccess file.

Someone please point me in the right direction.

---

### Post by beep3 on 2014-12-23
Not sure, but it would surprise me if the *httpd.conf* file lives in */etc/httpd/conf*. Shouldn't the directory path be /etc/**apache2**/? Or is the server running CentOS rather than Ubuntu?

Might be worth doing a find for httpd.conf to check if the file lives somewhere else:

```
cd /etc/
find -type f -name httpd.conf
```

This may also help: [http://ubuntuforums.org/archive/index.php/t-1762721.html](http://ubuntuforums.org/archive/index.php/t-1762721.html)

---

### Post by cobras on 2014-12-23
Thanks beep2.  The find came up with nothing, maybe because the server is running CentOS.  Turns out the command I needed was 'httpd -l', which returned 
Compiled in modules:
  core.c
  mod_authn_file.c
  mod_authn_default.c
  mod_authz_host.c
  mod_authz_groupfile.c
  mod_authz_user.c
  mod_authz_default.c
  mod_auth_basic.c
  mod_auth_digest.c
  mod_reqtimeout.c
  mod_include.c
  mod_deflate.c
  mod_log_config.c
  mod_logio.c
  mod_env.c
  mod_expires.c
  mod_headers.c
  mod_unique_id.c
  mod_setenvif.c
  mod_version.c
  mod_ssl.c
  worker.c
  http_core.c
  mod_mime.c
  mod_dav.c
  mod_status.c
  mod_autoindex.c
  mod_suexec.c
  mod_cgid.c
  mod_dav_fs.c
  mod_negotiation.c
  mod_dir.c
  mod_actions.c
  mod_userdir.c
  mod_alias.c
  mod_rewrite.c
  mod_so.c

Now I need to figure out if the modules I need are there, and if not how to enable them.  Slowly and not so surely, but I'll get there.

Thanks.

---

