---
title: "cyrus-imapd suddenly not starting"
date: 2015-04-28
forum: General Help
---

### Post by zijn on 2015-04-28
Ubuntu server 14.04.2
Linux poseidon 2.6.32-042stab088.4 #1 SMP Thu Apr 3 17:41:05 MSK 2014 x86_64 x86_64 x86_64 GNU/Linux
cyrus-imapd-2.4 (2.4.17+caldav~beta9-3)


After rebooting my server yesterday (after a package upgrade having nothing to do with cyrus afaict) cyrus-imapd is silently failing. The logs complain that the socket does not exist:

status=deferred (connect to poseidon.xxxx.com[/run/cyrus/socket/lmtp]: No such file or directory)

Indeed, there's nothing cyrus related in /var/run (/run). In /etc/init.d/cyrus-imapd:

NAME=cyrmaster
DAEMON=/usr/sbin/${NAME}
PIDFILE="/var/run/${NAME}.pid"

Attempting to manually start it tells me nothing:

# service cyrus-imapd status [or start]
[no response]


None of the cyrus or postfix configs have been altered recently. I see nothing in any log to suggest a problem upon startup.

/etc/cyrus.conf:
START {
  recover         cmd="/usr/sbin/cyrus ctl_cyrusdb -r"
  #idled          cmd="idled"
  #mupdatepush   cmd="/usr/sbin/cyrus ctl_mboxlist -m"
  delprune        cmd="/usr/sbin/cyrus expire -E 3"
  tlsprune        cmd="/usr/sbin/cyrus tls_prune"
}

SERVICES {
  imap            cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
  imaps           cmd="imapd -s -U 30" listen="imaps" prefork=0 maxchild=100
  #pop3            cmd="pop3d -U 30" listen="pop3" prefork=0 maxchild=50
  #pop3s          cmd="pop3d -s -U 30" listen="pop3s" prefork=0 maxchild=50
  nntp            cmd="nntpd -U 30" listen="nntp" prefork=0 maxchild=100
  #nntps          cmd="nntpd -s -U 30" listen="nntps" prefork=0 maxchild=100

  #lmtp           cmd="lmtpd" listen="localhost:lmtp" prefork=0 maxchild=20
  #lmtp            cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
  lmtpunix        cmd="lmtpd" listen="/run/cyrus/socket/lmtp" prefork=0 maxchild=20

  sieve           cmd="timsieved" listen="localhost:sieve" prefork=0 maxchild=100
  notify          cmd="notifyd" listen="/var/run/cyrus/socket/notify" proto="udp" prefork=1
  #mupdate       cmd="mupdate" listen=3905 prefork=1
  #mupdate       cmd="mupdate -m" listen=3905 prefork=1
  #imap           cmd="proxyd" listen="imap" prefork=0 maxchild=100
  #imaps          cmd="proxyd -s" listen="imaps" prefork=0 maxchild=100
  #pop3           cmd="pop3proxyd" listen="pop3" prefork=0 maxchild=50
  #pop3s          cmd="pop3proxyd -s" listen="pop3s" prefork=0 maxchild=50
  #lmtp           cmd="lmtpproxyd" listen="lmtp" prefork=1 maxchild=20
}

EVENTS {
  checkpoint      cmd="/usr/sbin/cyrus ctl_cyrusdb -c" period=30
  delprune        cmd="/usr/sbin/cyrus expire -E 3" at=0401
  expunge         cmd="cyr_expire -X 8" at=0600
  tlsprune        cmd="/usr/sbin/cyrus tls_prune" at=0401
  #squatter_1     cmd="/usr/bin/nice -n 19 /usr/sbin/cyrus squatter -s" period=120
  #squatter_a     cmd="/usr/sbin/cyrus squatter" at=0517
}

Note the lmtp/lmtpunix lines. At some point i made a change, then a second one. Unfortunately, that was a long time ago and i stupidly didn't leave any comments here. However, everything has been working well for several years.


/etc/imapd.conf:

configdirectory: /var/lib/cyrus
proc_path: /run/cyrus/proc
mboxname_lockpath: /run/cyrus/lock
lmtpsocket: /run/cyrus/socket/lmtp
idlesocket: /run/cyrus/socket/idle
notifysocket: /run/cyrus/socket/notify
syslog_prefix: cyrus

I do have socket and lock dirs under /var/lib/cyrus but they were last modified several years ago and seem to be left over from some other config. Other dirs there have seen more recent activity. Everything seems to be pointing towards the socket & lock dirs being created under /run but there's nothing there.

I found this bug report from the previous version which seems to be related:

[http://www.ubuntuupdates.org/package/core/trusty/universe/base/cyrus-imapd-2.4](http://www.ubuntuupdates.org/package/core/trusty/universe/base/cyrus-imapd-2.4)


Finally, the following is from apt-history log for the update done yesterday. I've included everything regardless of whether i know it's of consequence. I also rebooted the server afterwards so it's entirely possible that the package upgrades have nothing to do with the problem with cyrus.

amd64 (2.88dsf-41ubuntu6, 2.88dsf-41ubuntu6.1)
apache2-bin:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apache2-data:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apache2-doc:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apache2-mpm-prefork:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apache2-utils:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apache2.2-bin:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apache2:amd64 (2.4.7-1ubuntu4.1, 2.4.7-1ubuntu4.4)
apt-utils:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.7)
apt:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.7)
ca-certificates:amd64 (20130906ubuntu2, 20141019ubuntu0.14.04.1)
dpkg-dev:amd64 (1.17.5ubuntu5.3, 1.17.5ubuntu5.4)
dpkg:amd64 (1.17.5ubuntu5.3, 1.17.5ubuntu5.4)
dselect:amd64 (1.17.5ubuntu5.3, 1.17.5ubuntu5.4)
e2fslibs:amd64 (1.42.9-3ubuntu1, 1.42.9-3ubuntu1.2)
e2fsprogs:amd64 (1.42.9-3ubuntu1, 1.42.9-3ubuntu1.2)
gnupg:amd64 (1.4.16-1ubuntu2.1, 1.4.16-1ubuntu2.3)
gpgv:amd64 (1.4.16-1ubuntu2.1, 1.4.16-1ubuntu2.3)
isc-dhcp-client:amd64 (4.2.4-7ubuntu12, 4.2.4-7ubuntu12.1)
isc-dhcp-common:amd64 (4.2.4-7ubuntu12, 4.2.4-7ubuntu12.1)
language-pack-en-base:amd64 (14.04+20140707, 14.04+20150219)
language-pack-en:amd64 (14.04+20141110, 14.04+20150219)
libapache2-mod-php5:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
libapt-inst1.5:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.7)
libapt-pkg4.12:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.7)
libasn1-8-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libc-bin:amd64 (2.19-0ubuntu6.5, 2.19-0ubuntu6.6)
libc-dev-bin:amd64 (2.19-0ubuntu6.5, 2.19-0ubuntu6.6)
libc6-dev:amd64 (2.19-0ubuntu6.5, 2.19-0ubuntu6.6)
libc6:amd64 (2.19-0ubuntu6.5, 2.19-0ubuntu6.6)
libcomerr2:amd64 (1.42.9-3ubuntu1, 1.42.9-3ubuntu1.2)
libcups2:amd64 (1.7.2-0ubuntu1.2, 1.7.2-0ubuntu1.5)
libcupsfilters1:amd64 (1.0.52-0ubuntu1.2, 1.0.52-0ubuntu1.4)
libcupsimage2:amd64 (1.7.2-0ubuntu1.2, 1.7.2-0ubuntu1.5)
libdpkg-perl:amd64 (1.17.5ubuntu5.3, 1.17.5ubuntu5.4)
libfreetype6:amd64 (2.5.2-1ubuntu2.3, 2.5.2-1ubuntu2.4)
libgcrypt11:amd64 (1.5.3-2ubuntu4.1, 1.5.3-2ubuntu4.2)
libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.1, 2.12.23-12ubuntu2.2)
libgnutls26:amd64 (2.12.23-12ubuntu2.1, 2.12.23-12ubuntu2.2)
libgssapi3-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libhcrypto4-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libheimbase1-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libheimntlm0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libhx509-5-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libicu52:amd64 (52.1-3, 52.1-3ubuntu0.2)
libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libkrb5-26-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libmysqlclient18:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
libroken18-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libss2:amd64 (1.42.9-3ubuntu1, 1.42.9-3ubuntu1.2)
libssl-dev:amd64 (1.0.1f-1ubuntu2.8, 1.0.1f-1ubuntu2.11)
libssl-doc:amd64 (1.0.1f-1ubuntu2.8, 1.0.1f-1ubuntu2.11)
libssl1.0.0:amd64 (1.0.1f-1ubuntu2.8, 1.0.1f-1ubuntu2.11)
libtasn1-6:amd64 (3.4-3ubuntu0.1, 3.4-3ubuntu0.2)
libtiff5:amd64 (4.0.3-7ubuntu0.1, 4.0.3-7ubuntu0.3)
libudev1:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11)
libwbclient0:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
libwind0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1, 1.6~git20131207+dfsg-1ubuntu1.1)
libxext6:amd64 (1.3.2-1, 1.3.2-1ubuntu0.0.14.04.1)
libxrender1:amd64 (0.9.8-1, 0.9.8-1build0.14.04.1)
linux-libc-dev:amd64 (3.13.0-45.74, 3.13.0-49.83)
multiarch-support:amd64 (2.19-0ubuntu6.5, 2.19-0ubuntu6.6)
mysql-client-5.5:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
mysql-client-core-5.5:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
mysql-common:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
mysql-server-5.5:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
mysql-server-core-5.5:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
mysql-server:amd64 (5.5.41-0ubuntu0.14.04.1, 5.5.43-0ubuntu0.14.04.1)
openssl:amd64 (1.0.1f-1ubuntu2.8, 1.0.1f-1ubuntu2.11)
patch:amd64 (2.7.1-4ubuntu1, 2.7.1-4ubuntu2)
php-pear:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-cli:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-common:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-dev:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-gd:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-intl:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-mysql:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-pspell:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-readline:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5-sqlite:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
php5:amd64 (5.5.9+dfsg-1ubuntu4.6, 5.5.9+dfsg-1ubuntu4.9)
python-samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
samba-common-bin:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
samba-common:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
samba-dsdb-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
samba-libs:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
samba-vfs-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.5, 4.1.6+dfsg-1ubuntu2.14.04.7)
sudo:amd64 (1.8.9p5-1ubuntu1, 1.8.9p5-1ubuntu1.1)
sysv-rc:amd64 (2.88dsf-41ubuntu6, 2.88dsf-41ubuntu6.1)
sysvinit-utils:amd64 (2.88dsf-41ubuntu6, 2.88dsf-41ubuntu6.1)
tcpdump:amd64 (4.5.1-2ubuntu1.1, 4.5.1-2ubuntu1.2)
tzdata:amd64 (2015a-0ubuntu0.14.04, 2015d-0ubuntu0.14.04)
udev:amd64 (204-5ubuntu20.10, 204-5ubuntu20.11)

---

