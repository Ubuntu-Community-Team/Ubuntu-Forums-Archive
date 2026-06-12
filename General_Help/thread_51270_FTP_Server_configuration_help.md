---
title: "FTP Server configuration help"
date: 2005-07-23
forum: General Help
---

### Post by scorpio2002 on 2005-07-23
Hi there! I can't get vsftpd to work. I installed it and I went into the configuration file to set a few things up. As the server was not working, I uninstalled it and then I deleted the vsftpd.conf file. Then I reinstalled vsftpd but it didn't create an new vsftpd.conf fine.

Where can I get one?

---

### Post by uggy on 2005-07-23
[QUOTE=scorpio2002]Hi there! I can't get vsftpd to work. I installed it and I went into the configuration file to set a few things up. As the server was not working, I uninstalled it and then I deleted the vsftpd.conf file. Then I reinstalled vsftpd but it didn't create an new vsftpd.conf fine.

Where can I get one?[/QUOTE]
 I think this is the default file:

yannick@yop:~$ cat /etc/vsftpd.conf.ORI |grep -v \#
listen=YES
anonymous_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
yannick@yop:~$

---

### Post by scorpio2002 on 2005-07-23
Well, now it works again. Anyway, I'd like the file with all the comments so that I know what I can change.

What I would obtain is:

1) anonymus login allows people to go into the anonymous dir only. They can only download and not upload;

2) being able to create users dedicated to the FTP server that have their own dir in which they can upload and download files.

will you help me?
Donato

---

### Post by charlieg on 2005-07-23
[QUOTE=scorpio2002]will you help me?[/QUOTE]
Can't you help yourself?  It's not like [vsftpd](http://vsftpd.beasts.org) is not [documented](http://vsftpd.beasts.org/vsftpd_conf.html).  Back up your working conf file and then play / tweak according to that page (which is, incidentally, just the man page rendered in html).

---

### Post by scorpio2002 on 2005-07-23
> Can't you help yourself?
Oh, well, I'm sorry, you're right :P I'm a bit lazy :-)

---

### Post by scorpio2002 on 2005-07-23
Well, looks like I can't do it myself after all.

Now I can't even run vsftpd. Look at what happens:

```
skorpio@skorpio:~$ sudo /etc/init.d/vsftpd start
skorpio@skorpio:~$
```

Basically I don't get any message when I try to run it and if I check with ps I can't see any vsftpd process. 

I thought this was due to some settings I applied, but I went back to the old conf file and it's still not working. :|

It's gonna drive me crazy :(

---

### Post by scorpio2002 on 2005-07-23
Well, it's working again. :|

Anyway, I can't get the anonymous user to upload. That's what happens;
```

ftp> put back.doc
local: back.doc remote: back.doc
200 PORT command successful. Consider using PASV.
553 Could not create file.
```

This is my conf file:

```

# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
listen=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
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
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
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
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
```

Why it doesn't allow the anonymous user to upload?

---

### Post by blu.gecko on 2005-07-23
well Im not sure about that application but here is a good referance to your issue.

[http://ubuntuguide.org/#installftpserver](http://ubuntuguide.org/#installftpserver) :grin:

---

### Post by scorpio2002 on 2005-07-24
Ok, I found out why it didnt work, it was a matter of priviledges :-)

---

