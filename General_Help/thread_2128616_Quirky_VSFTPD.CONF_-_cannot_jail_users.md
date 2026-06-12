---
title: "Quirky VSFTPD.CONF - cannot jail users"
date: 2013-03-23
forum: General Help
---

### Post by RaHorakhty on 2013-03-23
For some reason my vsftpd.conf file allows the system users,  added using useradd and groupadd commands to browse other directories - even though I set the jailed option.  Can anyone figure out what I did wrong in vsftpconf.  I  want clients to RW and browse just one directory!  Its like vsftp auto logs into the root directory.  Here’s how it looks:

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
#local_umask=022
use_localtime=YES
xferlog_enable=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

---

### Post by RaHorakhty on 2013-04-08
101+ views and not one reply! THIS IS JOKE &#8211; whatever happened to the concept of UBUNTU! I got sick of waiting for you pansies, so I decided to brew my own tut for Debian (Ubu and BT).  It&#8217;s really not as confusing as it seems.  You don&#8217;t have bloat your system with Apache server and utilities like chkconfig.  Here&#8217;s how you can DIY to share your mp3s in just 7 easy steps, forget about the 101 opts in vsftpd.conf for now.  

**1.**    Install vsftpd &#8211; [COLOR=#ff0000]sudo apt-get install vsftpd [/COLOR]and [COLOR=#ff0000]open-ssl[/COLOR]  and [COLOR=#ff0000]FileZilla[/COLOR] and then reboot.


**2.**    Make sure FTP is active by running either nmap localhost or service - -status-all &> services.txt or ftp localhost. You might need to install the actual ftp program at this point.


**3.**    Create a fake shell to help jail (restrict) users.   Adding a &#8220;fake&#8221; shell edit the /etc/shells file and add a non-existent shell name like /bin/false, for example.  This fake shell will limit access on the system for FTP users , edit the shells file.


```
sudo root gedit /etc/shells


# /etc/shells: valid login shells
/bin/sh
/bin/bash
/bin/false
```


/bin/false is our added no-existent shell. With RH Linux, a special device name /dev/null exists already. Don't forget to bkup and save! 


**4. **   Add user(s) and set the proper permissions on the file directory. For simplicity lets work with &#8220;ftpuser&#8221;.  root and a handful of other usernames are not permitted login via ftp by default. The list of names are typically found in file **/etc/vsftpd/ftpusers** and/or **/etc/vsftpd/user_list.** This is because of the (default) clear-text nature of FTP leaving the root user's password freely obtainable to anyone along the path with even the slightest interest of capturing clear-text passwords.
  
```
mkdir -p /home/ftp/ftpuser
useradd ftpuser -d /home/ftp/ftpuser/ -s /bin/false
passwd ftpuser
chown ftpuser /home/ftp/ftpuser
chmod 700 /home/ftp/ftpuser
```


**5.**    Back up and modify VSFTPD.CONF as root.  IT&#8217;S ALL ABOUT VSSFTPD.CONF. You have to gut the entire file and replace it with the following :


```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
#local_umask=022  #change to 077 if you want your uploaded files avail with a mask of 700
use_localtime=YES
xferlog_enable=YES
chroot_local_user=YES

secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```


Don&#8217;t forget to save  the file as root! Reboot vsftp server


 ```
services vsftpd restart
```


See if you can login as ftpuser.  If you cant then go back to step one or check your firewall settings.  You might have to change your firewall rules so that it works with FTP.


**6. **    Now its time for SSL/TLS.  Make sure open SSL/TLS is installed!   


```
apt-get install vsftpd openssl
```


Once that&#8217;s set change add the following lines right _*[COLOR=#ff0000]**ABOVE**[/COLOR]*_ &#8220;rsa_cert_file=/etc/ssl/private/vsftpd.pem&#8221;


```
ssl_enable=YES
allow_anon_ssl=YES
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH
```


Save the file as root! Now generate a key using the following:


```
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem
```


reboot vsftp server!


```
services vsftpd restart
```


**7. **    Use the site manager in FZ to select TLS/AES to login and test ftpuser.  You can probably use lftp and ftp-ssl, but I bet you&#8217;re probably tired of typing by now.  Stay tuned for my next tutorial. I&#8217;ll demo how to harden the server using different opts and ciphers.  Have a good one!

---

