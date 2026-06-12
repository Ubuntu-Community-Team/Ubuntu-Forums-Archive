---
title: "Setting Up Server To Receive Photo Uploads From Form"
date: 2007-12-12
forum: General Help
---

### Post by merrydown on 2007-12-12
I have been trying unsuccessfully for 3 days to get my gutsy server to accept uploads.  I thought I had all the settings correctly configured, but the form just returns empty rather than completing the upload when I submit it.

Has anyone got a checklist I can use to determine if everything is set up right?

FORM TAG
---------------------------------------------------------:
<FORM METHOD="POST" NAME="formToUpload" id="formToUpload" enctype="multipart/form-data" action="add.php">

(The directory the file is going to has permissions 777)

PHP.INI SNIPPITS
---------------------------------------------------------
Registered PHP Streams 	zip, php, file, data, http, ftp, compress.bzip2, compress.zlib, https, ftps

post_max_size	16M	16M

upload_tmp_dir	/tmp	/tmp

Loaded Modules 	core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_include mod_mime mod_negotiation mod_php5 mod_rewrite mod_setenvif mod_ssl mod_status mod_suexec

HTTP_ACCEPT 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

SERVER["HTTP_ACCEPT"]	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

file_uploads	On	On

ANY help much appreciated

---

