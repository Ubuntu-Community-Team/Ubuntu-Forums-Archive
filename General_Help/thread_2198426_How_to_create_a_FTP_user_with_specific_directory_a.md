---
title: "How to create a FTP user with specific directory access only"
date: 2014-01-08
forum: General Help
---

### Post by ssaththiyan on 2014-01-08
Hi, 

I have to configure FTP server for our customer access to download the files. But I don't want to give them to see all the directories. Say i have customer ABC, PQR, XYZ, these customers will have FTP assess with different user name and password, When they log in to ftp using ftp client they have to see only the directories that  i have created  for them. Say i have created  /home/ ABC, home/PQR, home/XYZ. 

They shouldn't go to any other directories and access. I tried to configure[FONT=Consolas]**chroot_local_user=YES** option and it didn't let me longin again. the error message i got was [/FONT][B]500 OOPS: vsftpd: refusing to run with writable root inside chroot()

can any one help me on how to do this task? 

my vsftpd.conf file looks like this 

[/B]anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xfarlog_enable=YES
chroot_local_user=YES( there is two of this available but i uncomment this only) 
secure_chroot_dir=/var/run/vsftpd/empty
pam_services_name=vsftpd

---

