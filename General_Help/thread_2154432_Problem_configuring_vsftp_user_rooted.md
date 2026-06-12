---
title: "Problem configuring vsftp user rooted"
date: 2013-06-14
forum: General Help
---

### Post by mickey13 on 2013-06-14
I'm having a problem getting my vsftpd server configured the way I would like.  I'm using vsftpd version=3.0.2.  At the moment it will function when chroot_local_user=NO, but chroot_local_user=YES is a requirement.

I get the following error using the lftp client:

ls: Fatal error: gnutls_record_recv: An unexpected TLS packet was received.

I've googled this quite a bit, and nothing has worked for me yet.  I am using ssl:

ssl_enable=YES
ssl_ciphers=HIGH

Any suggestions?

---

### Post by mickey13 on 2013-06-14
I get a similar error with FileZilla version 3.5.3:

```
Status:	Connecting to <my.external.ip.address>:990...
Status:	Connection established, waiting for welcome message...
Response:	220 FTP Banner
Command:	AUTH TLS
Response:	234 Proceed with negotiation.
Status:	Initializing TLS...
Status:	Verifying certificate...
Command:	USER <username>
Status:	TLS/SSL connection established.
Response:	331 Please specify the password.
Command:	PASS **************************************
Error:	GnuTLS error -15: An unexpected TLS packet was received.
Error:	Could not connect to server
```

---

### Post by carboi82 on 2013-06-14
This perhaps might help... 
[https://bbs.archlinux.org/viewtopic.php?id=162824](https://bbs.archlinux.org/viewtopic.php?id=162824)

---

### Post by mickey13 on 2013-06-16
Thanks for your reply.  I've come across that post before.  In their setup they have chroot_list_enable=YES, whereas in my setup, I have chroot_list_enable=NO.  So I don't need the chroot_list file; though I've tried setting chroot_list_enable=YES and created the file just to be sure.

Also, I do have:

```
pasv_enable=YES
pasv_min_port=my.min.ftp.data.port
pasv_max_port=my.max.ftp.data.port
pasv_address=my.external.ip.address

```

Any other suggestions?

---

### Post by mickey13 on 2013-06-17
Here's my /etc/vsftpd.conf; is there a glaring error that's causing this chroot to fail?  As mentioned before, if I set chroot_local_user=NO, the service functions properly.  But when I set chroot_local_user=YES, I get the above error (it is a requirement that users are jailed to their home directory).  Thanks.

Here are some notes about the setup:
[LIST]
[*]PAM authentication
[*]Security certificate
[*]Passive mode enabled
[/LIST]

```
listen=YES
anonymous_enable=NO
local_enable=YES
virtual_use_local_privs=YES
write_enable=YES
local_umask=0022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
dual_log_enable=YES
log_ftp_protocol=YES
connect_from_port_20=NO
nopriv_user=ftp_user
ftpd_banner=blah

chroot_local_user=YES
chroot_list_enable=NO

secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd.virtual
guest_enable=YES
hide_ids=YES
force_dot_files=YES
hide_file=NO
max_per_ip=2
max_clients=20
pasv_enable=YES
pasv_min_port=my.min.ftp.data.port
pasv_max_port=my.max.ftp.data.port
pasv_address=<externalIpAddress>
user_sub_token=$USER
local_root=/<vsftpdHome>/$USER
user_config_dir=/etc/vsftpd/vusers
ssl_enable=YES
ssl_ciphers=HIGH
listen_port=990
debug_ssl=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
require_ssl_reuse=NO
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
rsa_cert_file=<certFile>
rsa_private_key_file=<keyFile>

```

---

### Post by mickey13 on 2013-06-17
I've also seen people report that the following does not work, but I haven't come across a reason as to why that is:

```
chroot_local_user=YES
ssl_ciphers=HIGH

```

---

### Post by mickey13 on 2013-06-17
Found my answer here:  [http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update](http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update)

I added the following setting:

```
allow_writeable_chroot=YES
```

I think this applies to vsftpd version 3.0 or higher, which looks like is installed via apt-get since version 13.04.

Hope this saves someone else some time.  Took me forever :/

---

### Post by aaron41 on 2014-05-11
> **mickey13 said:**
> Found my answer here:  [http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update](http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update)

I added the following setting:

```
allow_writeable_chroot=YES
```

I think this applies to vsftpd version 3.0 or higher, which looks like is installed via apt-get since version 13.04.

Hope this saves someone else some time.  Took me forever :/

Saved me loads of time, thank you very much! =D

---

### Post by Hakunka-Matata on 2014-06-27
allow_writeable_chroot=YES
Thank you heaps, I've been searching for this answer too!  das

---

