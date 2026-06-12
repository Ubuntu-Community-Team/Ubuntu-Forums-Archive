---
title: "ftp primission"
date: 2005-08-02
forum: General Help
---

### Post by HAMM3R on 2005-08-02
Hey.  I have another question.  I got vsftpd running.  I made it so people who are logged in can write to their home directory.  However, every file uploaded onto the ftp has the wrong primissions.  When i try to access them through my browser, (i use apache2) i get a 403 (no primissions).  I have looked in the apache config file, and its not a problem with apache.  Why is every uploaded file have the wrong primissions?  Bellow is my vsftpd.conf file.  I REALLY hope someone can help.  Thanks!

```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
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
local_umask=077
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
ftpd_banner=Welcome to the HAMM3R.net FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
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

---

### Post by heimo on 2005-08-02
You can try changing the mask value to what it suggests in the configuration file. That probably fixes it. Remember to restart the service after configuration changes. (sudo /etc/init.d/vsftpd restart)

---

### Post by HAMM3R on 2005-08-02
[QUOTE=heimo]You can try changing the mask value to what it suggests in the configuration file. That probably fixes it. Remember to restart the service after configuration changes. (sudo /etc/init.d/vsftpd restart)[/QUOTE]
 do you mean changing local_umask=077 to local_umask=022  ?

---

### Post by heimo on 2005-08-02
[QUOTE=HAMM3R]do you mean changing local_umask=077 to local_umask=022  ?[/QUOTE]

Yes.

---

### Post by HAMM3R on 2005-08-02
thanks!!  It worked.

---

### Post by HAMM3R on 2005-08-02
I almost forgot.  I have another question.   For some reason, when uploading multiple files, it will frequently freeze during the ftp upload.  I know its not a bandwitdth problem.   Is there some setting that may limit the size of uploads or anything?  If i recall correctly, it was less than a 1 MB file that it froze on.  It HAS happened multiple times.  So any idea with this problem?  Thanks!

---

### Post by heimo on 2005-08-02
No idea.. I'd try different ftp clients and try to reproduce the problem. I'd maybe run protocol analyzer Ethereal same time and watch for any reasons at the moment hangup happens. You could also try moving large files with some other protocol (http, nfs, smb) and see if the problem is actually ftp related at all. Also check ifconfig for any errors - and /var/log/messages and possibly vsftpds own log (where ever that is) for any errors and warnings.

---

### Post by HAMM3R on 2005-08-02
Ok now im in trouble.  I tried a few other ftpds and had even more problems with them.  Im back to vsftpd.  All the other ftpds i tried ARE removed now.  But when i try to connect to the ftp now, i get:  421 Service not available, remote server has closed connection

And that's from localhost ^^.  It didnt work on windows either.  So now i have more problems than i began with.  :(   What do i do now?

---

### Post by heimo on 2005-08-02
Erhm... I suggested trying other clients, not servers - but anyway, find where vsftpd puts its log file. You need to know that anyway. It's somewhere under /var/log/, probably /var/log/vsftpd.log or similar. Try restarting it sudo /etc/init.d/vsftpd restart

If that doesn't help, take a copy of the configuration file and do complete reinstall of vsftpd. 
 ```
sudo apt-get remove --purge vsftpd
sudo apt-get install vsftpd

```

---

### Post by HAMM3R on 2005-08-02
Well this is interesting:

hamm3r@hamm3r:/var/log$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd
No /usr/sbin/vsftpd found running; none killed.                                                                                                        [ ok ]
 * Starting FTP server: vsftpd                                                                                                                         [ ok ]
hamm3r@hamm3r:/var/log$


**I didnt find anything in the log.  It seems vsftpd isnt even starting

---

### Post by heimo on 2005-08-02
Or it just wasn't running before and that's why stopping failed. You can try to restart it again (should see it stopping ok), or use *ps aux | grep vsftpd *or *netstat *to see if process is alive and listening to ftp port. Or ... you could just try connecting with client - I don't know if you already tried?

---

### Post by HAMM3R on 2005-08-02
ps aux | grep vsftpd:
hamm3r    8103  0.0  0.3   3032   720 pts/0    S+   07:04   0:00 grep vsftpd

nmap:
21/tcp   open  ftp

Looks like it is listening.... but look at this:

hamm3r@hamm3r:/etc$ sudo /etc/init.d/vsftpd stop
 * Stopping FTP server: vsftpd
No /usr/sbin/vsftpd found running; none killed.                                                                                                        [ ok ]
hamm3r@hamm3r:/etc$ sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                                                                                                         [ ok ]
hamm3r@hamm3r:/etc$ sudo /etc/init.d/vsftpd stop
 * Stopping FTP server: vsftpd
No /usr/sbin/vsftpd found running; none killed.                                                                                                        [ ok ]
hamm3r@hamm3r:/etc$ sudo /etc/init.d/vsftpd start
 * Starting FTP server: vsftpd                                                                                                                         [ ok ]

---

### Post by heimo on 2005-08-02
And how about this one?
netstat -ltp

---

### Post by HAMM3R on 2005-08-02
I see:

tcp        0      0 *:ftp                   *:*                     LISTEN     -

---

### Post by heimo on 2005-08-02
Hmm... I was hoping for name of a program. 

I would do:
```
sudo /etc/init.d/networking restart
``` 

And check that you don't have any of those other ftp servers running.

---

### Post by HAMM3R on 2005-08-02
Well that didnt say much, just:

hamm3r@hamm3r:/etc$ sudo /etc/init.d/networking restart
Password: XXXXXXXXX
 * Reconfiguring network interfaces...                                                                                                                 [ ok ]

---

### Post by heimo on 2005-08-02
That's aboutwhat it shoud say. ;) No news is good news. I'm puzzled, it could be that something has "reserved" the port, but if you don't know which process, you can't get rid of it. netstat could help you on that, but it didn't show what I was hoping for. Frankly, I would reboot and see if it has any effect.

And make sure that no other ftp servers are installed / starts on boot.

---

### Post by HAMM3R on 2005-08-02
Ok.  I reinstalled using --pruge to remove.  I backed up the config file, and replaced it once vsftp was done installing, and guess what....

hamm3r@hamm3r:/etc$ sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd
No /usr/sbin/vsftpd found running; none killed.                                                                                                        [ ok ]
 * Starting FTP server: vsftpd                                                                                                                         [ ok ]

 ](*,)

Edit:  i did reboot previously.  How can i get a list of all running apps to see if any other ftpds are running?

This too:

D:\Documents and Settings\HAMM3R>ftp 10.0.0.2 
Connected to 10.0.0.2.
Connection closed by remote host.

*10.0.0.2 is my internal IP for my linux box

---

### Post by heimo on 2005-08-02
Well... go find that log file and check /var/log/messages too. It's not fun to debug blindly. Or check if you can pass some "verbose" flags to that process, usually -v

---

### Post by HAMM3R on 2005-08-02
AHA.  It's working.  It's wierd what i had to do.  I wanted to make sure proftpd and pure-ftpd (which i had installed previously) were completely removed.  So i had to INSTALL them, then remove them with --purge.  I did that with both, then re-installed vsftpd, and it worked!  I still have a problem with it freezing, but ill work on that.  Im just glad this is working now.  Thank you SO MUCH heimo!!!

Regards,
Austin

---

