---
title: "trouble with vsftpd and ubuntu 16"
date: 2017-08-03
forum: General Help
---

### Post by majed17 on 2017-08-03
Peace, I managed to get vsftpd working but the problem is with ie11. in this browser, the whole catalogue is displayed, not just the home directory; from etc to var. 
in opera and firefox it works great.
here is the configuration:

```
listen=YES

listen_ipv6=NO

anonymous_enable=NO

local_enable=YES

write_enable=YES

local_umask=022

#anon_upload_enable=YES

#anon_mkdir_write_enable=YES

dirmessage_enable=YES

use_localtime=YES

xferlog_enable=YES

connect_from_port_20=YES

#chown_uploads=YES
#chown_username=whoever

#xferlog_file=/var/log/vsftpd.log

#xferlog_std_format=YES

#idle_session_timeout=600
.
#data_connection_timeout=120

#nopriv_user=ftpsecure

#async_abor_enable=YES


ftpd_banner=Welcome to the FTP service. Learn from mistakes, otherwise scram!
.
#deny_email_enable=YES

#banned_email_file=/etc/vsftpd.banned_emails

# chroot_list_enable below.
#chroot_local_user=YES

# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist
userlist_deny=NO


#ls_recurse_enable=YES

secure_chroot_dir=/var/run/vsftpd/empty

pam_service_name=vsftpd

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO

#utf8_filesystem=YES
```

in vsftpd.userlist:
```
ftp
```
what have i done wrong?

---

