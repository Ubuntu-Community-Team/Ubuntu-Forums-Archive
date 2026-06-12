---
title: "vsftpd for user of www-data group"
date: 2015-10-30
forum: General Help
---

### Post by alain.roger on 2015-10-30
Hello,

I use my local computer as web development machine.
So i have installed LAMP stack and my local user is added to www-data group.
However,all files/directories under /var/www are owned by www-data user and group, and when i run my IDE it can not overwrite or create any file/directory under /var/www.
Therefore as my IDE allow my to connect to /var/www as FTP i was thinking to install vsftpd and setup everything to make it works.

Like that all my files/directories from webserver can be synchronized with a "local" copy under my $HOME directory, that coulb be later on used for GIT versioning tool.

My issue is that i can not the write way to setup vsftpd in order to use my local user/password and that it will have access and permission as www-data group.

can you help me please ?
thx

---

### Post by Lars Noodén on 2015-10-30
There are two questions.  

First, it is unsafe to give www-data write access to any files or directories which are served by the web server.  Sometimes there are exceptions, permanent or temporary, for specific files, but the general idea is that the user and group are there to provide an unprivileged user with read access to the web material.  So, what problem are you trying to solve with the user or group ownerships?

Second, FTP is quite unsafe these days (since 1995 or so).  It transmits all login information and data unencrypted for anyone between you and your server to intercept and reuse.  It is also fairly hard to set up.  On the other hand, SFTP support is part of the package OpenSSH-server and provides a secure replacement / upgrade from FTP.  So, can your IDE support SFTP instead?

---

### Post by alain.roger on 2015-10-30
1. as i wrote, it is only on my local machine so i'm the only one to have access to it.
as www-data (user and group) are the only one to have access to /var/www i add my local linux user to the www-data group. So i can operate on files/directories there.

my IDE is PHPstorm and i'm testing the following situation: to have a remote (fake remote for now) from PHPstorm to a webserver in order to replicate file/directory structure in my HOME directory, debug/creates/modify files and synchronize back updated files/directories to web server.
if this work i will purchase a license for PHPstorm, if it does not work... i will try another IDE.
I used during 3 years Eclipse, but it has some bug for remote debugging unfortunately.

2. PHPstorm support SFTP and SSH connection to synchronize web structure (directory/file) to a local directory in HOME folder e.g. and them synchronizes changes to web server

---

### Post by Lars Noodén on 2015-10-30
1.  Great.  If you are the only user, then you can chown /var/www to your user and group so that you can write it and www-data cannot.  All that matters is that www-data can read it, and with the o=rx for directories and o=r for files, which is the default, it can.  However, if at a later date you start to share write access with other users, then you should make a separate group for that. 

2.  Since PHPstorm can use SFTP, I would look that direction instead.  As mentioned, the package openssh-server provides SFTP support.  It does so out of the box and is much less of a pain to set up than vsFTPd.

---

