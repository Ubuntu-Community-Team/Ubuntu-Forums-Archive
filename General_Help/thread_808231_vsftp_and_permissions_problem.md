---
title: "vsftp and permissions problem"
date: 2008-05-26
forum: General Help
---

### Post by jessika-kaos on 2008-05-26
I am having a lot of trouble setting up an FTP server. Whenever I try to log in I am ujnable to get a directory listing for the shared directories. I get "550 Failed to change directory."

The shared directories are on an NTFS partition and I have symlinks to them in /home/ftp. 

vsftpd.conf:
```
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=sonne
ftpd_banner=Ph'nglui mglw'nafh Cthulhu R'lyeh wgah'nagl fhtagn!
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp
local_umask=077
```

fstab:
```
# /etc/fstab: static file system information.
#/dev/sdb1	
UUID=A6A01A87A01A5DDD /media/Files	ntfs-3g	rw,auto,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
#/dev/sda1
UUID=8CDC156CDC1551B6 /media/Windows	ntfs-3g	rw,auto,user,fmask=0111,dmask=0000   0   0

```

and here are the results of ls  -ld:

lrwxrwxrwx 1 root root   19 2008-05-25 21:33 files -> /media/Files/
d-wx-wx-wx 2 ftp  root 4096 2008-05-25 21:31 upload

Any ideas please? I've looked all over but can't seem to find a solution that works.

---

### Post by Grognot on 2008-05-26
From [http://www.vsftpdrocks.org/faq/](http://www.vsftpdrocks.org/faq/)
> Q) Why don't symlinks work with chroot_local_user=YES?
A) This is a consequence of how chroot() security works. As alternatives,
look into hard links, or if you have a modern Linux, see the powerful
"mount --bind".

---

