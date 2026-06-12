---
title: "vsftp, can't upload big files"
date: 2016-02-02
forum: General Help
---

### Post by cknipe on 2016-02-02
Hi All,


I have a small (anon) vsftp server.  When I upload small files, the upload succeeds.  When I upload bigger files, the upload fails... 


For example:
```
root@host:/home/src# ls -l /etc/sysctl.conf 
-rw-r--r-- 1 root root 2062 Jan  4 03:48 /etc/sysctl.conf
root@host:/home/src# perl test.pl /etc/sysctl.conf 
FTPStore() (0.138 Seconds) File 83a9680a618f2a3566dcc9c4315c5761 stored on server
```

And on the server, the xferlog shows:
```
Tue Feb  2 16:39:34 2016 1 198.19.252.205 2826 /8/83/83a/83a9680a618f2a3566dcc9c4315c5761 a _ i a -anonymous@ ftp 0 * c

```

Sizes differ, because the files are BASE64 encoded prior to uploading.


Now when I take a bigger file... 
```
root@host:/home/src# ls -l /home/cknipe/src/myfile.tar.gz 
-rw-rw-r-- 1 cknipe cknipe 0 Jan 20 21:13 /home/cknipe/src/myfile.tar.gz
root@host:/home/src# perl test.pl /home/cknipe/src/myfile.tar.gz 
FTPStore() (0.472 Seconds) Article 3debba782c4be066a564556e1b0e74f2 stored on server
```

xferlog shows:
```
Tue Feb  2 16:40:32 2016 1 198.19.252.205 0 /3/3d/3de/3debba782c4be066a564556e1b0e74f2 a _ i a -anonymous@ ftp 0 * c

```

And yes - /3/3d/3de/3debba782c4be066a564556e1b0e74f2 is 0 bytes, nothing has been written to the file.


I am at a complete loss as to why uploads work, but why bigger files do NOT work.  From a debug output on the bigger file in the client:

```
root@host:/home/src# perl test.pl /home/cknipe/src/myfile.tar.gz 
Net::FTP>>> Net::FTP(2.77)
Net::FTP>>>   Exporter(5.68)
Net::FTP>>>   Net::Cmd(2.29)
Net::FTP>>>   IO::Socket::INET(1.33)
Net::FTP>>>     IO::Socket(1.36)
Net::FTP>>>       IO::Handle(1.34)
Net::FTP=GLOB(0x2eb2750)<<< 220 Welcome to the FTP service.
Net::FTP=GLOB(0x2eb2750)>>> USER anonymous
Net::FTP=GLOB(0x2eb2750)<<< 331 Please specify the password.
Net::FTP=GLOB(0x2eb2750)>>> PASS ....
Net::FTP=GLOB(0x2eb2750)<<< 230 Login successful.
Net::FTP=GLOB(0x2eb2750)>>> CWD /3/3d/3de
Net::FTP=GLOB(0x2eb2750)<<< 250 Directory successfully changed.
Net::FTP=GLOB(0x2eb2750)>>> PORT 198,19,252,205,170,214
Net::FTP=GLOB(0x2eb2750)<<< 200 PORT command successful. Consider using PASV.
Net::FTP=GLOB(0x2eb2750)>>> STOU 3debba782c4be066a564556e1b0e74f2
Net::FTP=GLOB(0x2eb2750)<<< 150 FILE: 3debba782c4be066a564556e1b0e74f2.1
Net::FTP=GLOB(0x2eb2750)<<< 226 Transfer complete.
Net::FTP=GLOB(0x2eb2750)>>> QUIT
Net::FTP=GLOB(0x2eb2750)<<< 221 Goodbye.

```

vsftp accepts the file 100% fine and dandy.  No errors, what so ever.


Why is are the uploads failing?


vsftpd.conf:
```
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=NO
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/xferlog
xferlog_std_format=YES
idle_session_timeout=30
data_connection_timeout=30
nopriv_user=ftp
async_abor_enable=YES
ftpd_banner=Welcome to the FTP service.
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
seccomp_sandbox=NO

```

Thnx,
Chris.

---

### Post by cknipe on 2016-02-02
Nevermind... 1D10T moment... :D

---

