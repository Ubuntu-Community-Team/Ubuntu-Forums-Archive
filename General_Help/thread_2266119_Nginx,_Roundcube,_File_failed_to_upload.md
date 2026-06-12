---
title: "Nginx, Roundcube, File failed to upload"
date: 2015-02-20
forum: General Help
---

### Post by axetone on 2015-02-20
Hi,
  I have Roundcube installed on Ubuntu 14.04, using NGINX, with static IP, SpamAssassin, ClamAV -and everything is sending/receiving fine including downloads...however cannot upload anything to send.


*****PHP.ini


memory_limit = 256M
max_execution_time = 60
;open_basedir =
log_errors = On
post_max_size = 100M
file_uploads = On
upload_tmp_dir = /tmp
upload_max_filesize = 100M


*****Folder Permissions
/tmp
srw-rw---- 1 nginx nginx


/mail/temp
drwxrwxrwx  2 nginx nginx   4096 Feb 20 00:41 temp


*****Nginx.conf
under http directive...
client_max_body_size 100m;


-----------
****ERRORS
-note: output below I removed domain, and directory names.


FastCGI sent in stderr: "PHP message: PHP Warning:  File upload error - unable to create a temporary file in Unknown on line 0" while reading response header from upstream, client: X.X.X.X server: domain.com, request: "POST /mail/?_task=mail&_id=~~~from=compose&_action=upload HTTP/1.1", upstream: "fastcgi://unix:/tmp/php5-fpm.sock:", host: "domain.com", referrer: "https://domain.com/mail/?_task=mail&_action=compose&_id:~~~~




----------
****TROUBLESHOOTING
I've set the mail/temp folder to 777 just to see if it would write a file there, and it did, but Roundcube still gave the error "File Upload Failed". Normally, that directory /mail/temp is set to 755 and would write 0kb files as opposed to 777 a file actually would be written...error in roundcube remains same either way. I also played around with the root (PHP pointed) /tmp directory permissions to see is 777 would help (all files mentioned are accessible by nginx:nginx)  ...no joy, same error output by Roundcube: "File Upload Failed". As a last resort I pointed PHP to the same /mail/temp to see if it would write, it did but still -same roundcube error "File Upload Failed".


Anyone? Please and Thank You!!

---

