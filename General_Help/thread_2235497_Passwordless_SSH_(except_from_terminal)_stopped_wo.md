---
title: "Passwordless SSH (except from terminal) stopped working"
date: 2014-07-21
forum: General Help
---

### Post by bjtuna on 2014-07-21
I'm running 14.04.  This morning I found that my passwordless SSH logins via public key are no longer working when the calls are being made by applications. I can reproduce this with FileZilla (attempting to connect to a remote host via SFTP) and Komodo Edit (attempting to open a remote filesystem).  The remote hosts are properly configured; I've used ssh public key authentication for years without problems.  I am still able to ssh from a terminal.

FileZilla's error is "Authentication failed."

Komodo Edit's error log is:


```
[2014-07-21 09:20:11,168] [DEBUG] places_js: waiting for document complete
[2014-07-21 09:20:11,815] [DEBUG] koSFTPConnection: __init__()
[2014-07-21 09:20:11,819] [DEBUG] koSFTPConnection: open: s:HHHHHHHHH p:22 u:XXXXXXX
[2014-07-21 09:20:12,531] [WARNING] koSFTPConnection: do_authenticateWithPassword:: SSHException: Authentication failed.
[2014-07-21 09:20:12,532] [WARNING] koSFTPConnection: SSH error: Invalid username/password
[2014-07-21 09:20:12,533] [DEBUG] koSFTPConnection: open: s:HHHHHHHH p:22 u:XXXXXXX
[2014-07-21 09:20:14,471] [DEBUG] koSFTPConnection: authinfo: got back 'XXXXXXX:'
[2014-07-21 09:20:14,672] [WARNING] koSFTPConnection: do_authenticateWithPassword:: SSHException: Authentication failed.
[2014-07-21 09:20:14,673] [WARNING] koSFTPConnection: SSH error: Invalid username/password
[2014-07-21 09:20:14,673] [DEBUG] koSFTPConnection: open: s:HHHHHHH p:22 u:XXXXXXX
[2014-07-21 09:20:15,452] [INFO] koSFTPConnection: SFTP: Login cancelled by user.

```

This was working last week when I left the office. I did perform an apt-get upgrade over the weekend, here is the appropriate entry from /var/log/apt/history.log:

```
Start-Date: 2014-07-19  10:18:00
Commandline: aptdaemon role='role-commit-packages' sender=':1.658'
Install: linux-image-extra-3.13.0-32-generic:amd64 (3.13.0-32.57), linux-image-3.13.0-32-generic:amd64 (3.13.0-32.57), linux-headers-3.13.0-32-generic:amd64 (3.13.0-32.57), linux-headers-3.13.0-32:amd64 (3.13.0-32.57)
Upgrade: libavformat54:amd64 (9.13-0ubuntu0.14.04.1, 9.14-0ubuntu0.14.04.1), linux-headers-generic:amd64 (3.13.0.30.36, 3.13.0.32.38), mysql-server-core-5.5:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), mysql-server-5.5:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), liblwp-protocol-https-perl:amd64 (6.04-2, 6.04-2ubuntu0.1), mysql-client-core-5.5:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), mysql-client:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), libdecoration0:amd64 (0.9.11+14.04.20140423-0ubuntu1, 0.9.11.1+14.04.20140701-0ubuntu1), compiz-gnome:amd64 (0.9.11+14.04.20140423-0ubuntu1, 0.9.11.1+14.04.20140701-0ubuntu1), compiz-core:amd64 (0.9.11+14.04.20140423-0ubuntu1, 0.9.11.1+14.04.20140701-0ubuntu1), file:amd64 (5.14-2ubuntu3, 5.14-2ubuntu3.1), libmagic1:amd64 (5.14-2ubuntu3, 5.14-2ubuntu3.1), compiz:amd64 (0.9.11+14.04.20140423-0ubuntu1, 0.9.11.1+14.04.20140701-0ubuntu1), libcompizconfig0:amd64 (0.9.11+14.04.20140423-0ubuntu1, 0.9.11.1+14.04.20140701-0ubuntu1), xdg-utils:amd64 (1.1.0~rc1-2ubuntu7, 1.1.0~rc1-2ubuntu7.1), libswscale2:amd64 (9.13-0ubuntu0.14.04.1, 9.14-0ubuntu0.14.04.1), mysql-client-5.5:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), language-pack-gnome-en:amd64 (14.04+20140522, 14.04+20140707), mysql-common:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), libmysqlclient18:amd64 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), libmysqlclient18:i386 (5.5.37-0ubuntu0.14.04.1, 5.5.38-0ubuntu0.14.04.1), compiz-plugins-default:amd64 (0.9.11+14.04.20140423-0ubuntu1, 0.9.11.1+14.04.20140701-0ubuntu1), libavcodec54:amd64 (9.13-0ubuntu0.14.04.1, 9.14-0ubuntu0.14.04.1), transmission-gtk:amd64 (2.82-1.1ubuntu3, 2.82-1.1ubuntu3.1), language-pack-en-base:amd64 (14.04+20140410, 14.04+20140707), language-pack-gnome-en-base:amd64 (14.04+20140410, 14.04+20140707), linux-libc-dev:amd64 (3.13.0-30.55, 3.13.0-32.57), transmission-common:amd64 (2.82-1.1ubuntu3, 2.82-1.1ubuntu3.1), language-pack-en:amd64 (14.04+20140522, 14.04+20140707), libminiupnpc8:amd64 (1.6-3ubuntu2, 1.6-3ubuntu2.14.04.1), linux-image-generic:amd64 (3.13.0.30.36, 3.13.0.32.38), libavutil52:amd64 (9.13-0ubuntu0.14.04.1, 9.14-0ubuntu0.14.04.1), linux-generic:amd64 (3.13.0.30.36, 3.13.0.32.38)

```

One potentially useful bit:  when I first installed 14.04, I could not get passwordless SSH to work *at all*.  After some Google searching I found a workable "solution" was to add the following to my .bashrc:

```
SSH_AUTH_SOCK=`netstat -xl | grep -o '/run/user/1000/keyring-.*/ssh$'`
[ -z "$SSH_AUTH_SOCK" ] || export SSH_AUTH_SOCK
```

Also:  I created a new user on my system and was unable to reproduce the problem on that user. So it must be something to do with my primary user's environment.  I am wondering what could have changed.

---

