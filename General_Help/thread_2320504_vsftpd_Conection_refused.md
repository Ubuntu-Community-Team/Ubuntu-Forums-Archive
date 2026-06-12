---
title: "vsftpd Conection refused"
date: 2016-04-14
forum: General Help
---

### Post by gusdudu on 2016-04-14
hellow from spain, muy server ubuntu r14, "conection refused" in ftp localhost command.

any ideas? thanks


**this is my config:**

listen=YES
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
idle_session_timeout=600
data_connection_timeout=120
async_abor_enable=YES
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=FTP CIBERIOS
deny_email_enable=YES
banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
ls_recurse_enable=NO
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certificates/vsftpd.pem
rsa_private_key_file=/etc/ssl/certificates/vsftpd.pem
ssl_enable=YES
allow_anom_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_tlsv2=YES
ssl_tlsv3=YES
requiere_ssl_reuse=NO
ssl_ciphers=HIGH

---

