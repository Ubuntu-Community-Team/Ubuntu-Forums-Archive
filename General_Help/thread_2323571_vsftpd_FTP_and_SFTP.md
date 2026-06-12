---
title: "vsftpd FTP and SFTP"
date: 2016-05-06
forum: General Help
---

### Post by gordon16 on 2016-05-06
Hello,

I have manage to get my vsftpd up and running with SSL.

How can I configure conf file so users are abel to login normal without any encryption and with?

So user can connect to 21 with encryption and 990 with?

Thank you.

Copy / past from part of my conf file:


listen_port=990

ssl_enable=Yes

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

allow_writeable_chroot=YES

#port_enable=NO

pasv_addr_resolve=NO

pasv_enable=YES
pasv_min_port=9000
pasv_max_port=9050

---

