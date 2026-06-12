---
title: "ftp help"
date: 2007-08-26
forum: General Help
---

### Post by AWerner32 on 2007-08-26
I recently set up an FTP server with gproftpd. i made a seperate user for use with it and set its home as the mount point for my external drive. i would like the ability to have a dropbox on the server where the people who use it can drop files or download files in it. i put a directory in the home area for that use however for some reason nobody can put anything into it or anything even though in gproftpd i gave the permissions to do everything to the folder. i really would like for this to work.

thanks in advance

---

### Post by AWerner32 on 2007-08-26
if it helps here is the server config file. i allowed everything thing in the directory /home/user/dropbox but i still cant drop files into it or anything


> ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTPD"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayFirstChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 1000
TransferRate STOR 43
TransferRate STOU 43
TransferRate APPE 43
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser user
  DenyALL
</Limit>

<Anonymous /home/user>
User user
Group ftp
AnonRequirePassword on
MaxClients 20 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
<Directory /home/user/dropbox>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Directory>
</Anonymous>



---

### Post by AWerner32 on 2007-08-27
nevermind i solved this, there were file ownership problems but i sorted them out

---

