---
title: "XAMPP install - how to make apache case insensitive"
date: 2007-01-20
forum: General Help
---

### Post by mrwooster on 2007-01-20
Hi,

I have installed lampp using XAMPP (its only for development purposes and so xampp made it easier) but am having problems with case sensitivity. I realise that this is a UNIX process, but there is a mod for apache called mod_speling which (i think) should make it case insensitive. 

As you can see from my httpd.conf the module seems to be loaded:

> LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authn_dbm_module modules/mod_authn_dbm.so
LoadModule authn_anon_module modules/mod_authn_anon.so
LoadModule authn_dbd_module modules/mod_authn_dbd.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule authz_dbm_module modules/mod_authz_dbm.so
LoadModule authz_owner_module modules/mod_authz_owner.so
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule file_cache_module modules/mod_file_cache.so
LoadModule cache_module modules/mod_cache.so
LoadModule disk_cache_module modules/mod_disk_cache.so
LoadModule mem_cache_module modules/mod_mem_cache.so
# mod_dbd doesn't work in Apache 2.2.3: getting always heaps of "glibc detected *** corrupted double-linked list" on shutdown - oswald, 10sep06
#LoadModule dbd_module modules/mod_dbd.so
LoadModule bucketeer_module modules/mod_bucketeer.so
LoadModule dumpio_module modules/mod_dumpio.so
LoadModule echo_module modules/mod_echo.so
LoadModule case_filter_module modules/mod_case_filter.so
LoadModule case_filter_in_module modules/mod_case_filter_in.so
LoadModule ext_filter_module modules/mod_ext_filter.so
LoadModule include_module modules/mod_include.so
LoadModule filter_module modules/mod_filter.so
LoadModule charset_lite_module modules/mod_charset_lite.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule logio_module modules/mod_logio.so
LoadModule env_module modules/mod_env.so
LoadModule mime_magic_module modules/mod_mime_magic.so
LoadModule cern_meta_module modules/mod_cern_meta.so
LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule ident_module modules/mod_ident.so
LoadModule usertrack_module modules/mod_usertrack.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
LoadModule mime_module modules/mod_mime.so
LoadModule dav_module modules/mod_dav.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule info_module modules/mod_info.so
LoadModule suexec_module modules/mod_suexec.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule cgid_module modules/mod_cgid.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule imagemap_module modules/mod_imagemap.so
LoadModule actions_module modules/mod_actions.so
**LoadModule speling_module modules/mod_speling.so**
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule apreq_module modules/mod_apreq2.so
LoadModule ssl_module modules/mod_ssl.so




However it still does not seem to be working. Is there anywhere else where I need to load the module or are there any other config files where the module might be disabled?

Thanks

Guy

---

### Post by JonnyR on 2007-01-20
Hi Guy,

Just checking, you have turned mod_spelling on in your httpd.conf?  The command to turn it on is:
```
CheckSpelling on
```

Taken from the ever helpful [Apache Documentation]("http://httpd.apache.org/docs/1.3/mod/") :) 

Jonny.

---

### Post by mooremic on 2008-04-30
The main problem with mod_speling is that it only modifies the GET on case for files, not directories. This is usually not the problem when migrating from a Windows seb server installation.  The problem is general URL case sensitivity.
Yes, you can set up a perl script to change all directories to lower-case, and search all scripts and html files to correct the broken links.  Been there, done that.  The problem still remains that long-time users of the sites have saved valuable links that no longer work.
I have found two possible solutions, neither of which I have been abel to get to work properly:
1.  Use Samba as a pass-through to make Apache case-insensive.  [http://linux.omnipotent.net/article.php?article_id=11710](http://linux.omnipotent.net/article.php?article_id=11710)
I understand the basic principles here.  Set up a Samba mountpoint on the directory and mount the Apache web directory to that mount point.  In theory, that would make the share case-insensitive.  The instructions are unclear and there are none of the usual comments and addenda to this post, leaving me to think it is unusable.  Anyone with details on setting this up on a newer system than this 2001 posting please chime in.

2. mod_nocase.c   This one scares me too much to try as I don't have any references from people who have tried it to tell me it is safe to use.  [http://www.misterblue.com/Software/mod_nocase.htm](http://www.misterblue.com/Software/mod_nocase.htm) 
Again, if anyone has details on where to put this file in an Ubuntu 8.04 system or comments on tracing the code, I would appreciate it.

A major goal of the Linux movement should be to make it easy to migrate off the Microsoft monster.  I have to believe this problem was solved years ago.  

Thank you for any advice.

---

