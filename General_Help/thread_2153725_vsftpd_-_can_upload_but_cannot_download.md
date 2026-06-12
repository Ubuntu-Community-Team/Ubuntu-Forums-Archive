---
title: "vsftpd - can upload but cannot download"
date: 2013-06-12
forum: General Help
---

### Post by PeterTaps on 2013-06-12
Folks,


Environment: Ubuntu 13.04


I have set up vsftpd to use virtual users as shown in [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293).


I have also downloaded the latest version of vsftpd from thefrontiergroup/vsftpd repository. The installed version is 2.3.5 
This version fixes "vsftpd refusing to run with writable root inside chroot" problem.


The directory to write to is /home/ftpdir and the user account for ftp is ftpusers.


Here is the content of /etc/vsftpd/ftpusers:


write_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
local_root=/home/ftpdir
chroot_local_user=YES
dirlist_enable=YES
download_enable=YES
guest_username=ftpusers
local_umask=022
file_open_mode=0666


When run, I am able to upload files from a ftp client. However, download fails with a "550 Failed to open file" error.


Here are the permissions on a file that is uploaded:


$ sudo ls -l /home/ftpdir
-rw------- 1 ftpusers ftpusers       9 Jun 12 01:13 3.txt


However, the same file cannot be downloaded.


If I manually chmod 666 on the file, the download works fine.


There are two issues here that I don't understand:


1. If the ftp client connection is chrooting to ftpusers, why upload works and not download?


2. Although my file open mode is set as 0666, why does the created file have just 600 mode?


I would appreciate it if someone can help me understand these issues.


Thank you in advance for your help.


Regards,
Peter

---

