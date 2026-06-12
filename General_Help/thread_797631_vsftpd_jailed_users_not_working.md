---
title: "vsftpd jailed users not working"
date: 2008-05-17
forum: General Help
---

### Post by ubunuub on 2008-05-17
Hi...Still a novice to Ubuntu :rolleyes: so I'm probably missing something obvious. But I can't get vsftpd jailing to work.

Following [these instructions]("http://ubuntuforums.org/showthread.php?t=518293&highlight=vsftpd") I have this as my /etc/vsftpd.conf

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
[B]chroot_local_user=YES
chroot_list_enable=NO[/B]
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

Then I do a ```
sudo useradd -d /home/testuser -m testuser
sudo passwd testuser

sudo /etc/init.d/vsftpd restart
```

I connect using Transmit FTP client on my Mac. But I can still browse to /.

I've looked everywhere I can think of for the solution. Hoping someone here can give a hand.

TIA

---

### Post by ubunuub on 2008-05-18
Bump :) Any suggestions? Thanks.

---

