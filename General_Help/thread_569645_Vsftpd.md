---
title: "Vsftpd"
date: 2007-10-07
forum: General Help
---

### Post by mattc908 on 2007-10-07
I installed VSFTPD but when I access the server I get this error when I log on anonymously: 

Server Said:
OOPS: vsftpd: refusing to run with writable anonymous root

I cant find anything that would fix this....

---

### Post by strider1551 on 2007-10-07
[This]("http://www.webservertalk.com/archive91-2004-3-159397.html") should be able to help you out.

Basically, the root directory for the ftp should be read only, but directories underneath it can be writable.

---

### Post by mattc908 on 2007-10-07
a couple of problems that is an older version and some of those features arnt in the /etc/vsftpd.conf folder........ And other FTP client that you recommend and how do I remove a program what is the command?

---

### Post by strider1551 on 2007-10-07
> a couple of problems that is an older version and some of those features arnt in the /etc/vsftpd.conf folder
From my understanding of the discussion in the link, I don't think it's the options so much as the folder permissions.  Let's say that the anonymous ftp root folder is /var/ftp.  /var/ftp should be read only.  Directories underneath it, such as /var/ftp/incoming could be made writable.

> And other FTP client that you recommend and how do I remove a program what is the command?
In the past I used proftpd, but at some point something made me switch to vsftpd.  I recommend you do your own research on what's out there.

As for removing a package, the command is:
```
sudo apt-get remove <packagename>
```
so in your case...
```
sudo apt-get remove vsftpd
```

("man apt-get" will give you a pretty complete understand of everything that apt-get can do)

---

### Post by mattc908 on 2007-10-08
Imma give vsftpd a shot so I get this error: OOPS: vsftpd: refusing to run with writable anonymous root.
This is whats enabled:
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

This is whats not:
#listen_ipv6=YES
#local_umask=022
#xferlog_enable=YES
#chown_uploads=YES
#chown_username= ftp
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
#ftpd_banner=Welcome to blah FTP service.
#deny_email_enable=YES
#chroot_local_user=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES


Those are all the possible configurations, so............?

---

### Post by strider1551 on 2007-10-08
Add another option, adjusting the directory to your preference:
```
anon_root=/var/ftp
```

Then set up the directories as follows and see where it gets you:
```
sudo mkdir /var/ftp
sudo mkdir /var/ftp/incoming
sudo chmod 775 /var/ftp/incoming
```

I'm not in a situation where I can test it myself, but vsftpd reloaded its config file without complaint when I added the option.

---

### Post by mattc908 on 2007-10-09
Hoorah!! Thanks alot!

---

### Post by mattc908 on 2007-10-09
New Problem: 
Server said:
Could not create file.

Error -160: could not start data transfer

---

### Post by strider1551 on 2007-10-10
Hmm... I seem to be having some trouble finding something on this, and unfortunately this is the busy day of the week for me.  I'll keep looking, but in the meantime if you could describe what's going on a little more (e.g., I assume this happens when you start a transfer?  It happens every time and wasn't a temporary problem? etc.)

---

### Post by mattc908 on 2007-10-10
It happens everytime it cant start a transfer.

---

### Post by mattc908 on 2007-10-13
Fixed that error a new one shows up: 
Server said:
Security: Bad IP connecting.

Error -160: could not start data transfer

---

