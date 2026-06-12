---
title: "Backup script no longer can send files to my Ubuntu server"
date: 2019-09-16
forum: General Help
---

### Post by Doulos1 on 2019-09-16
Ubuntu 16.04

I really hope someone can help me figure this out.  Beginning sometime after July 24th I started getting the following message when trying to transfer my backups to my server - this has worked flawlessly since installation May 2018.  My system was updated July 27.  I didn't realize these connections were being refused until a week ago when I tried to get one of my previous backups.

```
Backups directory already exists
Backing up Files and Directories for clanfga.com
Initiating FTP connection to send backup
Connected to 74.91.117.247 (74.91.117.247).
220 (vsFTPd 3.0.3)
331 Please specify the password.
230 Login successful.
250 Directory successfully changed.
200 Switching to Binary mode.
local: /home/mywebsite/backups/mywebsite.com-09-14-2019.tar.gz remote: mywebsite.com-09-14-2019.tar.gz
227 Entering Passive Mode (74,91,117,247,201,235).
ftp: connect: Connection refused
221 Goodbye.
```

Here is my vsftpd config file
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
listen=NO
#
# This directive enables listening on IPv6 sockets. By default, listening
# on the IPv6 "any" address (::) will accept connections from both IPv6
# and IPv4 clients. It is not necessary to listen on *both* IPv4 and IPv6
# sockets. If you want that (perhaps because you want to listen on specific
# addresses) then you must run two copies of vsftpd with two configuration
# files.
listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default).
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
#local_umask=022
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
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
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
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
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
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
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
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd

# Enable Passive mode
pasv_enable=Yes

#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO

#
# Uncomment this to indicate that vsftpd use a utf8 filesystem.
#utf8_filesystem=YES
seccomp_sandbox=NO

```
Any hlep would be greatly appreciated.

---

### Post by #&amp;thj^% on 2019-09-16
Usally the error is caused due to the misconfiguration of the passive port range on the FTP server and in the firewall settings.
Try to add the following line.
```

PassivePortRange 30000 35000
```

Now restart the Pureftp service.
```

service pureftpd restart
```

Even if the FTP server allows passive ports, the firewall can block the connection between FTP client and server when the passive port range is not open. It results in 227 entering passive mode ftp connect connection timed out error.

For firewall like Iptables, add the entry like,
```

iptables -I INPUT -p tcp --dport 49152:65534 -j ACCEPT
```

Now restart iptables:
```

service iptables save
```
Hope this helps!

---

### Post by TheFu on 2019-09-16
Plain FTP?   Sending credentials, unencrypted, like that is too scary.  Also, it is possible to "pull" backups, so the backup server storage isn't nearly as easily hacked.  If you can't switch from plain FTP.

Would you consider using a secure way to transfer the files? Perhaps scp or rsync?  ssh, sftp, scp, rsync, and most of the best Unix backup tools on linux will support the ssh-keys.  And *pulling* the backups is a better method.

For one file:
```
scp      userid@remote:/home/mywebsite/backups/mywebsite.com-*.tar.gz     /Backup/storage/
```
Creates secure keys from your local client machine:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote 
```
The 2nd command pushes the public key to the other machine.  This assumes ssh is setup by the provider.

Grabbing a tgz file, is less efficient than mirroring the website using rsync, but that would be a larger change.

---

### Post by #&amp;thj^% on 2019-09-16
> **TheFu said:**
> 

Would you consider using a secure way to transfer the files? Perhaps scp or rsync?  ssh, sftp, scp, rsync, and most of the best Unix backup tools on linux will support the ssh-keys.  And *pulling* the backups is a better method.

+1 I could not agree more with TheFu's suggestion.

---

### Post by Skaperen on 2019-09-16
+1 more.  secure is the way to go, even if on your own LAN.  be ready to move it anywhere by already being secure.

---

### Post by Doulos1 on 2019-09-18
Thanks for your replies.  I tried converting the script I use to secure, but couldn't figure it out.
I will try your suggestions as soon as I get a chance.

Thanks, again.

---

### Post by TheFu on 2019-09-18
> **Doulos1 said:**
> Thanks for your replies.  I tried converting the script I use to secure, but couldn't figure it out.
I will try your suggestions as soon as I get a chance.

Thanks, again.

The 1 line - scp - that I showed is a "pull", not a push. It runs on the local machine, not the remote one.  The ssh-keygen and ssh-copy-id commands are run on your local Linux machine, not the remote one.

So, if you have a tar.gz script creating backups on the remote machine every night at 2am and that takes 5 minutes.  Wait until 2:30am to run the "pull" from your local workstation.  You your use ssh from the local workstation to run the remote tar.gz creation script.  That is extremely common.

---

### Post by Doulos1 on 2019-09-18
The local machine (generates backups) is a CentOS 7 webserver running cPanel, the remote machine (receiving backups) is Ubuntu 16.04 - if that matters.

---

### Post by Doulos1 on 2019-09-18
Thank you. I successfully was able to use rsync to sync the entire website (public_html) to the remote server.  But, it is asking my for a password each time. How do I include the user password in my cron job to sync the public_html folder unattended on a weekly basis?

---

### Post by SeijiSensei on 2019-09-18
Use keys instead of a password: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Doulos1 on 2019-09-18
Here is the cron job I tried and the results when I used the same in terminal to test.> me@myserver.com [~]# ssh-keygen -t ed25519
ed25519.pub backup@74.91.117.247
rsync -r -a -v -e ssh --delete /home/mywebsite/public_html [email]backup@remoteipaddress:/home/remoteuser/remotefol.derGen[/email]erating public/private ed25519 key pair.
Enter file in which to save the key (/home/remoteuser/.ssh/id_ed25519): Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Saving key "ssh-copy-id -i ~/.ssh/id_ed25519.pub backup@remoteipaddress" failed: No such file or directory

---

### Post by TheFu on 2019-09-18
Dude.  backup@remoteipaddress is an example userid and IP. You are supposed to replace those with the correct values.  
The key parts are 1-time setups.  Only the scp/rsync needs to be in the crontab and it should be run from your local workstation, not from the hosting provider's system.

Also, I would NEVER EVER "push" backups from a remote host.  Always "pull" them, so you don't have to allow a system that you share with 3000 other people potential access to your personal workstation.

---

### Post by SeijiSensei on 2019-09-18
Create the key on the receiving host, typically for the same username as owns the files on the remote host to be transferred.  Transfer the key to that remote user. Then, as TheFu suggests, run rsync on the receiving host to suck down the files.

---

### Post by Doulos1 on 2019-09-18
> **TheFu said:**
> Dude.  backup@remoteipaddress is an example userid and IP. ...
I know that, I just use that in the example of my cron job.

---

### Post by Doulos1 on 2019-09-18
> **SeijiSensei said:**
> Create the key on the receiving host, typically for the same username as owns the files on the remote host to be transferred.  Transfer the key to that remote user. Then, as TheFu suggests, run rsync on the receiving host to suck down the files.

Exactly what I just did.  It works perfectly.

Thanks all.

---

### Post by TheFu on 2019-09-18
> **Doulos1 said:**
> Exactly what I just did.  It works perfectly.

Thanks all.

Happy you have a working solution.

rsync makes 1 copy.  Using almost the same format, you can have X versioned backups using rdiff-backup.

```
rsync -r -a -v -e ssh --delete /home/mywebsite/public_html \
      backup@remoteipaddress:/home/remoteu...motefol.der 

```
but
```
rsync -avz   --delete  me@myserver.com:public_html  \
 /local/backup/directory/www.example.com/
```
is the same using a "pull". Pulling is much more secure for the local workstation.

The **rdiff-backup** would be
```
rdiff-backup   --exclude-special-files   me@myserver.com:public_html  \
 /local/backup/directory/www.example.com/ 
```
rdiff-backup is basically an rsync that is efficient with versioning. It uses librsync and ssh and stores the most recent backup just like an rsync mirror. Older versions are diff.gz files for each change. Turns out to be extremely storage efficient.  rsync and rdiff-backup times should be comparable.  Basically, VERY fast unless some files change. I backup about 20 systems nightly using it.  Each system takes about 2-8 minutes, normally. Each has between 60 and 180 days of versioned backups depending on the risk mitigation required. A few times I've had to restore DB files from 40+ days ago, once from 73 days ago.

Both rsync and rdiff-backup use ssh for authentication and tunnelling of the data by default. rsync has since 2005 or so.  No need for* -e ssh* since then.

But the service provider would need have installed rdiff-backup or you could install it into your HOME/bin there and use it. Just depends on how far you want to go for having versioned backups.  The tgz solution provided versioning, so it is obviously worth having.  

Regardless, even if you are done with what you have now, glad it is working.

---

### Post by Doulos1 on 2019-09-18
Thanks, I will take another look at it when I get a chance.

---

