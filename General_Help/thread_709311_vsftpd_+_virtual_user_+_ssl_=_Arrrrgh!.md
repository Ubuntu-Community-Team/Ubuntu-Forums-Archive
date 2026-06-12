---
title: "vsftpd + virtual user + ssl = Arrrrgh!"
date: 2008-02-27
forum: General Help
---

### Post by iamtim on 2008-02-27
I am attempting to install vsftpd with virtual users on my webserver. I want secure logons and communication.

I can SSH in and access FTP with VU from a command line inside the box. So PAM authentication seems to be working. 

But every attempt to login externally with any TLS or SSL enabled secure client (FireFTP, FileZilla, Cyberduck)  returns "530 Please login with USER and PASS" error.

Do I give up and revert to local users without shells?
Is there a vsftpd.conf setting I am missing here?
Should I switch to Proftp?
Other thoughts?

---

### Post by iamtim on 2008-02-27
Whoops. Forgot my conf file.

local_enable=YES
write_enable=NO
local_umask=022
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
chroot_local_user=YES
guest_enable=YES
guest_username=virtual
listen=YES
listen_port=10021
pasv_min_port=10071
pasv_max_port=10073
ssl_enable=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
rsa_private_key_file=/etc/ssl/certs/vsftpd.pem

---

