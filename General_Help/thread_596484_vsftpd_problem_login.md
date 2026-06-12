---
title: "vsftpd problem login"
date: 2007-10-29
forum: General Help
---

### Post by txetxubcn on 2007-10-29
Hi from Spain! and sorry about my bad english
I installed vsftpd with apt-get and look a lot of forums to configurate ```
/etc/vsftp.conf
```
This is:
```

# Run standalone? vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=775
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that turning on ascii_download_enable enables malicious remote parties
# to consume your I/O resources, by issuing the command "SIZE /big/file" in
# ASCII mode.
# These ASCII options are split into upload and download because you may wish
# to enable ASCII uploads (to prevent uploaded scripts etc. from breaking),
# without the DoS risk of SIZE and ASCII downloads. ASCII mangling should be
# on the client anyway..
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to Txetxu FTP.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories. See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default. These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty. Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO
check_shell=NO
```

I use "useradd prueba" with pass "prueba". I put this user in ftp group that I created and home/prueba dir.
well... when I open ftp...
```
sergio@sergio-desktop:~$ ftp XXXXX.XX
Connected to XXXXX.XX.
220 FTPU ready.
Name (XXXXX.XX:sergio): prueba
331 Password required for prueba.
Password:
530 Login incorrect.
Login failed.
Remote system type is Ignored.

```
In the vsftpd.chroot_list appear the user "prueba"
I read in any forum that is problem of PAM and if I put /bin/false how login shell of "prueba" and this shell appear in /etc/shells the problem go over... but It not do.

my shell file is
```
# /etc/shells: valid login shells
/bin/csh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/sh
/usr/bin/screen
/bin/dash
/bin/bash
/bin/rbash
/bin/false
```

and my /etc/pam.d/vsftpd file is
```
# Standard behaviour for ftpd(8).
auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session

@include common-auth
auth	required	pam_shells.so

```


I prove more options, I can't log with my username of ubuntu (sergio) and neither with the user that I created recently (prueba)
If I put anonymous_enable=YES neither can login... :(

Can you help me please??

---

### Post by mannih2001 on 2007-10-31
Don't know if this is going to help, but my /etc/pam.d/vsftp looks like this:
```

#%PAM-1.0

# Uncomment this to achieve what used to be ftpd -A.
# auth       required     pam_listfile.so item=user sense=allow file=/etc/ftpchroot onerr=fail

auth     required       pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
# Uncomment the following line for anonymous ftp.
#auth    sufficient     pam_ftp.so
auth     required       pam_unix2.so
auth     required       pam_shells.so
account  required       pam_unix2.so
password required       pam_unix2.so
session  required       pam_unix2.so

```

---

### Post by gattu on 2008-03-19
Does anyone know how to fix 530 Login incorrect?????

I've soon spent three nights trying to fix this. I'm trying to use mysql to store my ftp accounts and if anyone know how I could use pam to test account athentification, I would be  happy.
But I guess the problem isn't concerning pam, since I **always** get 530 Login incorrect. It doesn't matter if I use encryption or not. Neither does it matter if I use an anonymous account, a local account or a guest account.

I've seen a lot of post about this problem but not really any solutions. Is there anyone that knows how to sort this out?

---

