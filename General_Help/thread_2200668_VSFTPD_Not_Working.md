---
title: "VSFTPD Not Working"
date: 2014-01-20
forum: General Help
---

### Post by yowchuan on 2014-01-20
Hi, I am trying to setup vsftpd.

Objective: To create virtual users so that each virtual users can login into their own specific directory.

Following guide written by [COLOR=#000000][FONT=verdana]Falko Timme[/FONT][/COLOR]: [http://www.howtoforge.com/virtual-hosting-with-vsftpd-and-mysql-on-ubuntu-12.04](http://www.howtoforge.com/virtual-hosting-with-vsftpd-and-mysql-on-ubuntu-12.04)

This is how my **/etc/vsftpd.conf** looks:
```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=vsftpd
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
guest_enable=YES
guest_username=vsftpd
local_root=/home/vsftpd/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf

```

Created virtual user: **virtual-diva**
```
# vsftpd per-user basis config file (override of any config option specified
# in the vsftpd server config file)
#
# TEMPLATE
#
# User virtual-diva- Description for user test
#


# Set local root
local_root=/home/web/public/virtual-diva.com/public/


# Disable any form of FTP write command.
# Allowed values: YES/NO
write_enable=YES

```

When I execute '**sudo vsftpd**' it gives me the following:
```
500 OOPS: could not bind listening IPv4 socket

```

When I execute '**sudo service vsftpd status**', I get the following, which means the vsftpd is running fine:
```
vsftpd start/running, process 25068

```

When I execute '**sudo netstat ap**', I get this for vsftpd process:
```
tcp        0      0 *:ftp                   *:*                     LISTEN      25068/vsftpd

```


When I execute 'sudo nano /var/log/vsftpd.log':

```
Mon Jan 20 01:53:35 2014 [pid 2] CONNECT: Client "my.ip.address"
Mon Jan 20 01:53:42 2014 [pid 2] CONNECT: Client "my.ip.address"
Mon Jan 20 01:53:42 2014 [pid 1] [virtual-diva] OK LOGIN: Client "my.ip.address"
Mon Jan 20 01:53:42 2014 [pid 2] CONNECT: Client "my.ip.address"
Mon Jan 20 01:53:43 2014 [pid 1] [virtual-diva] OK LOGIN: Client "my.ip.address"
Mon Jan 20 01:53:49 2014 [pid 3] [virtual-diva] FAIL MKDIR: Client "my.ip.address", "/wp-content/upgrade/wordpress-3.tmp"
Mon Jan 20 01:53:49 2014 [pid 3] [virtual-diva] FAIL RMDIR: Client "my.ip.address", "/wp-content/upgrade/wordpress-3.tmp"
Tue Jan 21 01:22:59 2014 [pid 2] CONNECT: Client "127.0.0.1"

```

When I try connecting to 'my.ip.address" using the login credentials I have created based on [the guide by Falko Timme]("http://www.howtoforge.com/virtual-hosting-with-vsftpd-and-mysql-on-ubuntu-12.04"), I just get time out/connection failed errors.

I have been trying to setup this for the past 3 days, but there doesn't seem to be anything I do that is changing the outcome.

Any insights and help will be greatly appreciated.

Thanks,
YC

---

