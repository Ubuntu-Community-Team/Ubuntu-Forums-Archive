---
title: "[SOLVED] Unable to connect to FTP Server"
date: 2007-10-15
forum: General Help
---

### Post by btaylor101 on 2007-10-15
I have installed vsftp and I am not able to connect to the server. When I try to connect using FileZilla from a windows pc I get an error stating Could not connect to server. I have opened port 20 on iptables. The vsftpd.conf file is below.

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=btaylor101
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

---

### Post by ruibernardo on 2007-10-15
If it is because of iptables, you should open port 21 and load the nf_conntrack_ftp module too. Port 20 shouldn't be necessary as it is vsftpd that uses that port later on the connection, not in a new connection attempt.

To check this, you should take a look at you log files for iptables errors (/var/log/messages by default), and also in the vsftpd log file to see if it is a vsftpd problem.

---

### Post by btaylor101 on 2007-10-15
That did the trick. I haven't read anything about choosing Port 21 so you were a life saver.

---

### Post by ruibernardo on 2007-10-15
Glad it worked :)

---

