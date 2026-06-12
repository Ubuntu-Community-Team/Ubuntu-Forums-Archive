---
title: "vsftpd, where do the upload download  files go?"
date: 2008-05-22
forum: General Help
---

### Post by sdowney717 on 2008-05-22
cant find this out
/var/ftp/pub??  /svr/ftp???
home something ftp???

upload download directory??
I got vsftpd running, but If I goto a url in the browser, [ftp://192.168.1.100](ftp://192.168.1.100) it gives me an index header BUT no files are listed.

---

### Post by bingoUV on 2008-05-22
1. Is vsftpd running at 192.168.1.100 ?

2. Are you using anonymous ftp? Then the listing should show files in /var/ftp. This directory should have permissions 755 though.

3. If it is not anonymous ftp but a local user's ftp account, files in his home directory should show up. World read and execute permission on the home directory are required.

Don't know about ftp users, but it should be something in vsftpd.conf.

---

### Post by sdowney717 on 2008-05-22
yes, it needs to be anonymous ftp
what would the chmod command line be?

---

### Post by bingoUV on 2008-05-22
```

sudo chmod -R 755 /var/ftp

```

---

### Post by sdowney717 on 2008-05-22
thanks
I chmoded the directory
I restarted vsftpd
sudo /etc/init.d/vsftpd restart

when I goto [ftp://192.168.1.100/](ftp://192.168.1.100/)

I still get no listing of files

---

### Post by bingoUV on 2008-05-22
Well, it should not even have needed a vsftpd restart. Have you made no changes to the /etc/vsftpd/vsftpd.conf?

One way to restore default behaviour is to remove vsftpd using Add/Remove Programs, remove /etc/vsftpd*
```

sudo rm -rf /etc/vsftpd*

```

and then install vsftpd again. Any customizations you have made to vsftpd.conf will be lost so you will need to make them again.

---

### Post by sdowney717 on 2008-05-22
Tried, it uninstalled and reinstalled
Tried it using terminal and synaptic
Still get no listing of the directory.
Any ideas?

---

### Post by bingoUV on 2008-05-22
1. Could it be that there is another ftp server is running on your machine? Stop the vsftpd and try accessing ftp server. Does it work?


2. From the machine that is running the vsftpd server, instead of giving the IP address try accessing [ftp://localhost/](ftp://localhost/). Does it work?

---

### Post by sdowney717 on 2008-05-22
are we sure that downloadable served files would go in 
/var/ftp?

What is ftpserver and how do you start it?

the localhost gives the same result, a header and no files listed.
This is my vsftp.conf file contents

# Access rights
anonymous_enable=YES
local_enable=YES
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
# Security
anon_world_readable_only=YES
connect_from_port_20=YES
hide_ids=YES
pasv_min_port=50000
pasv_max_port=60000
# Features
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES
# Performance
one_process_model=YES
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=50000

---

### Post by bingoUV on 2008-05-22
It has been /var/ftp in my experience with vsftpd which has been very long (10 years at the least).

To be sure, put the following line in /etc/vsftpd/vsftpd.conf
```

anon_root=/var/ftp

```
 and restart vsftpd

---

### Post by sdowney717 on 2008-05-22
still not showing

In my filesystem, the vsftpd.conf is in /etc, there is no /etc/vsftpd folder.

---

### Post by sdowney717 on 2008-05-22
connection refused?

scott@scott-desktop:~$ /etc/init.d/vsftpd stop
scott@scott-desktop:~$ /etc/init.d/vsftpd start
scott@scott-desktop:~$ ftp localhost
ftp: connect: Connection refused
ftp> exit
scott@scott-desktop:~$

tried this config and I can login ftp localhost at the prompt
```

listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=scott
idle_session_timeout=300
data_connection_timeout=120
ftpd_banner=Welcome to scott's FTP server
chroot_local_user=YES
chroot_list_enable=NO
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/home/scott
force_dot_files=YES
hide_ids=YES
max_per_ip=1
max_clients=6
pasv_min_port=1025
pasv_max_port=1125

```

but I dont know, still see nothing from firefox typing in [ftp://localhost](ftp://localhost)
BUT, I can do a dir and see files from the terminal when logging in
ftp localhost
then it asks for my user name and password

set local_root=/home/scott to local_root=/var/ftp shows the files in the directory

```

scott@scott-desktop:~$ ftp localhost
Connected to localhost.
220 Welcome to scott's FTP server
Name (localhost:scott): scott
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rwxrwxrwx    1 ftp      ftp            36 May 22 04:31 DSM320-VerInfo.txt
-rwxrwxrwx    1 ftp      ftp       4098504 May 22 04:31 FW-1.09
drwxrwxrwx    2 ftp      ftp          4096 May 22 18:05 pub
226 Directory send OK.
ftp> exit
221 Goodbye.

```

I can got to an xp machine and run ftp 192.168.1.100
and then I must login and it works.

BUT, it is not anonymous, it wants a user and password!

---

### Post by sdowney717 on 2008-05-22
[http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1211487210224+28353475&threadId=838752](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1211487210224+28353475&threadId=838752)

I finally solved this following the instruction here.

"anon_upload=YES only works when /var/ftp must be owned by owner and group root, and must have readonly permissions set for group, and others."

So i set the permissions on /var/ftp to only root. Others can only access files. Now I can ftp login with anonymous and no password

```

scott@scott-desktop:~$ ftp localhost
Connected to localhost.
220 Welcome to scott's FTP server
Name (localhost:scott): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rwxrwxrwx    1 ftp      ftp            36 May 22 04:31 DSM320-VerInfo.txt
-rwxrwxrwx    1 ftp      ftp       4098504 May 22 04:31 FW-1.09
drwxrwxr-x    2 ftp      ftp          4096 May 22 18:05 pub
drwxrwxr-x    2 ftp      ftp          4096 May 22 20:06 upload
226 Directory send OK.
ftp> exit
221 Goodbye.
scott@scott-desktop:~$ 

```

here is the vsftpd.conf file
I am wondering If I choose another directory location, then this problem might not have happened

```

listen=YES
anonymous_enable=YES
anon_root=/var/ftp
#anon_upload_enable=YES
anon_other_write_enable=YES
anon_mkdir_write_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
port_enable=YES
ftp_username=scott
connect_from_port_20=YES
chown_uploads=YES
chown_username=scott
idle_session_timeout=300
data_connection_timeout=120
ftpd_banner=Welcome to scott's FTP server
chroot_local_user=YES
chroot_list_enable=NO
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/home/scott
force_dot_files=YES
hide_ids=YES
max_per_ip=1
max_clients=6
pasv_min_port=1025
pasv_max_port=1125

```

Ok, I went on a windows PC and using IE, I can see the directory listing at [ftp://192.168.1.100](ftp://192.168.1.100)
Trying this using firefox on my local machine gives me nothing but the headers and no files listed

Why is that?

---

