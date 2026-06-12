---
title: "How to set up ProFTPd for home"
date: 2015-02-07
forum: General Help
---

### Post by Chelidze on 2015-02-07
[COLOR=#333333][FONT=UbuntuRegular]I want to create a home ftp server that I can excess from my pc that are using wifi.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]On windows I managed to do so by using filezila server, but on ubuntu I am running into problems, I installed the gadmin-proftpd gui software to help me but I can not create a ftp server.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So can you help me with the configurations what should I write in Ip address etc....[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thank you for your time.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Update[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I managed to access the log in page but now I am getting this error[/FONT][/COLOR]
```
[INDENT]530-Unable to set anonymous privileges.
530 Login incorrect.
[/INDENT]

```


This is the configurations I think I am using 

```
ServerType standaloneDefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTP Server"
ServerAdmin email@example.org
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
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
TLSOptions AllowClientRenegotiation
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser Levan
  DenyALL
</Limit>


<Anonymous /home/levan/Desktop/ffmpeg-git-20150124-64bit-static>
User Levan
Group Test
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  STOR STOU  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>



```

---

### Post by Lars Noodén on 2015-02-07
If you want it secure and easier to set up then I would [avoid FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and just use the built-in SFTP server that comes with openssh-server.  To do that just uninstall the FTP stuff and install [openssh-server](apt:openssh-server).  Then for basic use, that is all you need and you can continue to use FileZilla as your client.  And from your Ubuntu clients, you don't even need FileZilla, you can use any regular file manager to connect with SFTP.  Any user with a normal login will be able to connect via SFTP.  If you want to turn off remote shell access for some or all users, then that is an extra step but also easy.

---

### Post by Chelidze on 2015-02-07
Thank you for the reply but can I access SFTP server with web brosers ?? that is the reason I need the  ftp because I know browsers out of the box can enter it.
I love ssh but as far as I know people can not enter it with a web browser :)

---

### Post by Bucky Ball on 2015-02-07
Filezilla is available in Ubuntu. It is open-source and in the repositories (Software Centre).

---

### Post by Lars Noodén on 2015-02-07
Do you want read-only or read-write?  If you want to write, then SFTP is your only safe option.  If you want read-only, then you are better served with with HTTP and that is provided by nginx or apache2 instead.  

As Bucky Ball writes, FileZilla is in the repository.  If your users are on Ubuntu, then they don't even need FileZilla, just [open the file manager and press ctrl-L](https://www.youtube.com/watch?v=9S4DV1PluzA).  

Yes, I'm trying to find a way to avoid FTP.  ;)

---

