---
title: "vsftpd help"
date: 2007-02-15
forum: General Help
---

### Post by Brad D on 2007-02-15
I have vsftpd running on my xubuntu machine and I can connect ok with in my LAN but I can not connect from outside my network. I have forwarded ports 20 and 21 on my router. Any help would be appreciated. Here is my config file that I copied from an install tutorial.

# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=NO
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=brad
ftpd_banner=Welcome to Brad's FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
# anon_root=/home/ftp/

---

### Post by Brad D on 2007-02-16
Never mind I fixed it. I did my port forwarding on my router and neglected to click the enable box. Works great now.

---

