---
title: "Apache, VSFTPD, PHP - Owner Issues :: Easy Way to Inherit Ownership on Uploaded Files"
date: 2013-01-29
forum: General Help
---

### Post by own3mall on 2013-01-29
Hi All,

When a file is uploaded via FTP, the file owner is set to vsftpd while the group remains the same of www-data.  This is unacceptable, as a PHP chmod will fail every time with the owner of a file set to vsftpd.  I have file permissions set to 775, so why would a PHP chmod fail?  

Here is what is in my vsftpd.conf file:

```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
chown_uploads=YES
chown_username=www-data
file_open_mode=0775
local_umask=0002
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
local_root=/var/www/vhosts/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd_user_conf
local_max_rate=2000000 # bytes per sec, 2Mbytes per sec
max_clients=50 # to avoid DOS attack, if you have a huge server, increase this..
ftpd_banner=Welcome to vsFTPd Server, managed by Me

```It appears that PHP chmod will be successful if the owner of the file is set to www-data.  How do I get VSFTPD to set the default owner of an uploaded file to www-data?  Is there a way to use an ACL to have files inherit the owner of the directory recursively?  Or, is there something I can change in PHP's configuration to get chmod working based on who owns the file?

Right now, I'm using cron to set the owner and group to www-data every x hours, but there's got to be a better way.  

Please help!  It's appreciated.

---

### Post by adam.stokes on 2013-01-29
**chown_uploads** and **chown_username** only works for anonymously uploaded files. What you probably want is 'chmod g+s <directory>' where group is www-data for that directory. You'll also want to make sure the the files are writeable by those users in group 'chmod g+w <directory>'.

---

### Post by own3mall on 2013-01-30
> **adam.stokes said:**
> **chown_uploads** and **chown_username** only works for anonymously uploaded files. What you probably want is 'chmod g+s <directory>' where group is www-data for that directory. You'll also want to make sure the the files are writeable by those users in group 'chmod g+w <directory>'.

I am using chmod -R g+s <directory, but that doesn't help.  PHP CHMOD still fails.  It will not fail if the owner is correctly set to www-data instead of VSFTPD.   I don't think this has anything to do with the group, as it's not changing to begin with, and the files are 775 in terms of permissions.

Any other ideas?

---

### Post by adam.stokes on 2013-02-04
What user does php execute the chmod as? Whatever that user is will need to be in the group that has +rw access to those directory/files.

---

### Post by own3mall on 2013-07-07
After playing with various config settings and ideas, I've come up with an acceptable solution for virtual users.  Basically, all files uploaded by VSFTPD should be owned by the apache user www-data.  Once these files and directories are owned by www-data, PHP can chmod and chown without failing.  However, this change creates problems for FTP permission changing via FTP chmod commands.  Chmod commands issued through a FTP Client will not work, as the files are owned by www-data rather than vsftpd.  Only the owner user can change permissions on a file. 

> **adam.stokes said:**
> What user does php execute the chmod as? Whatever that user is will need to be in the group that has +rw access to those directory/files.

PHP execudes the chmod command as the apache user which is www-data.

So, how do I get both PHP chmod commands and FTP chmod commands to work together?  It would seem that I either need to tell apache to run as the ftpuser or tell VSFTPD to run using the apache user.  However, this doesn't seem possible.  Is there a way to get this done with virtual users?

---

### Post by own3mall on 2013-07-07
It looks like you could configure apache to run using the vsftpd account by changing the following in /etc/apache2/envvars:

```

export APACHE_RUN_USER=vsftpd

```

Then, you'd have to run the following command:

```

sudo chown vsftpd:www-data -R /var/lock/apache2

```

Now, php's chmod command will run under the vsftpd user, and so will chmod commands being issued by a client FTP program within a user's home directory.

The question is, how big of a security risk is this?  If the vsftpd account is hacked, apache files could be changed.  However, even if they were owned by www-data in the past, if the vsftpd account was somehow hacked, the files could have still been deleted or changed.  So did anything change security wise?

Here's what the vsftpd user shell is configured as:

```

vsftpd:x:4441:39::/var/www/vhosts:/bin/false

```

Any thoughts on this?

---

