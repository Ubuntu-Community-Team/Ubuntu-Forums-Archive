---
title: "Ubuntu Intentionally Sleeping when set to NEVER! Annoying WHY?"
date: 2020-01-10
forum: General Help
---

### Post by markackerman8@gmail.com on 2020-01-10
I will simply say this ...

1/ I have been helping people with Ubuntu for 10-15 years! ... So you can assume I know at least the average stuff!
...which leads to ...
2/ of course ALL settings are turned to OFF:
a/ Lock-OFF, 
b/ Automatic Suspend - OFF, Caffeine 
c/ Auto Suspend and Screen Saver Disabled

Other info 
1/ It is a Laptop that is PLUGGED IN!
2/ Ubuntu 18.04.3
3/ Kernel Linux 5.4.10-050410-generic x86_64
4/ Ubuntu Session WITH GDM!

Why do I say this! because ... in the past 3 months with this issue ... still happening
It has often been solved by going into the "Ubuntu" Session versus "Gnome on XORG" both with GDM

So either IT APPEARS to be an INTENTIONAL UBUNTU GLITCH - SO Annoying
-------------------------------------------------------------------------------------------------------------
What I have tried other than the above obvious stuff is
Sorry for its awkwardness

Screen Going Blank Problem
&#8728; 11/18/19
&#8728; Install Keep.Awake
&#8728; Prerequisites
&#8226; $ sudo apt install bzr libxss-dev libx11-dev libffi-dev python3-pip python3-netifaces python3-psutil xz-utils
&#8728; Suggested packages
&#8226; sudo apt install bzr-doc bzrtools python-bzrlib.tests  python-kerberos python-paramiko python-pycurl python-configobj-doc libkf5wallet-bin gir1.2-gnomekeyring-1.0 python-fs python-gdata python-keyczar python-testresources python-secretstorage-doc python-setuptools-doc
&#8226; sudo apt install graphviz librsvg2-bin fam   phonon4qt5-backend-gstreamer python-lzma-dbg   python-subunit  python-nose python-pyftpdlib python-gdata-doc   python-beaker python-mako-doc python-gssapi python-ply-doc libcurl4-gnutls-dev  python-pycurl-doc python-pyinotify-doc python-testtools-doc python-twisted 
&#8226; sudo apt install graphviz-doc libcurl4-doc libgnutls28-dev libidn11-dev libkrb5-dev libldap2-dev librtmp-dev libssh2-1-dev phonon-backend-gstreamer python-sqlalchemy python-pylibmc python-memcache python-pymongo python-redis python-funcsigs-doc python-coverage python-nose-doc
&#8226; sudo apt install krb5-doc libgcrypt20-doc gmp-doc libgmp10-doc libmpfr-dev gnutls-doc gnutls-bin krb5-user python-coverage-doc memcached python-pymongo-doc python-hiredis python-sqlalchemy-doc python-psycopg2 python-pymysql python-fdb python-pymssql
&#8226; sudo apt install libmpfr-doc libcache-memcached-perl  libanyevent-perl libyaml-perl libterm-readkey-perl  python-egenix-mxdatetime-doc  python-egenix-mxtools-doc python-fdb-doc python-gevent redis-server python-psycopg2-doc python-pymysql-doc
&#8226; sudo apt install libevent-perl libio-async-perl libjson-perl  libpoe-perl libtask-weaken-perl libyaml-shell-perl python-egenix-mxbeebase-doc python-egenix-mxproxy-doc python-egenix-mxqueue-doc python-egenix-mxstack-doc python-egenix-mxtexttools-doc python-egenix-mxuid-doc python-egenix-mxurl-doc python-gevent-doc  python-greenlet-doc python-greenlet-dev python-greenlet-dbg ruby-redis
&#8226; sudo apt install libcurses-perl libpoe-loop-event-perl libpoe-loop-tk-perl libsocket-getaddrinfo-perl
&#8728; and
&#8226; sudo pip3 install xprintidle
&#8728; cd /<your desired installation path>/
&#8226; cd /home/mark/Systems/Linux/Keep_Awake
&#8728; run
&#8226; bzr branch lp:keep.awak
&#8728; bzr: ERROR: Already a branch: "keep.awake"
&#8728; To run as a background service:
&#8226; nohup ./keepawake.py -r > /dev/null 2>&1 &
&#8728; GDM uses a separate dconf database to control power management. 
&#8728; You can make GDM behave the same way as user sessions by copying the user settings to GDM's dconf database.
&#8226; 
&#8226; sudo IFS=$'\n'; for x in $(sudo -u mark gsettings list-recursively org.gnome.settings-daemon.plugins.power); do eval "sudo -u gdm dbus-launch gsettings set $x"; done; unset IFS
&#8728; change your name from "mark", TOO MANY ERRORS, and access denied /mark/cache/dconf
&#8728; 11/17/19
&#8226; gsettings set org.gnome.desktop.session idle-delay 0
&#8226; sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
&#8226; gsettings set org.gnome.desktop.lockdown disable-lock-screen false
&#8226; gsettings set org.gnome.desktop.screensaver lock-enabled false
&#8226; sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
&#8226; sudo systemctl mask sleep.target  DID NOT WORK 
&#8227; To undo the change:
&#8226; sudo systemctl unmask sleep.target
&#8728; Or this for when on AC
&#8227; 0 for never
&#8226; gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
&#8227; On Battery
&#8226; gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 0
&#8728; For Login screen:
&#8226; gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
&#8728; Disable dimming screen when idle:
&#8226; gsettings set org.gnome.settings-daemon.plugins.power idle-dim false
&#8728; Nothing in the accepted answer has worked for me in 18.04. Instead I had to do the following:
&#8227; gsettings set org.gnome.settings-daemon.plugins.power idle-brightness 100

---

### Post by markackerman8@gmail.com on 2020-01-14
Well Proof is in the pudding!

For all those with Ubuntu "Auto Suspending" when EVERYTHING is set to the contrary, ...

... it is UBUNTU's intentional manipulation of your system! 

Pure and simple.

Ever since this post (0 views ... my butt LOL) ... caffeine has finally started working as it should!

That is the good news!

-----------------------------------------------------------
Now the better question is to what gain was Ubuntu doing this?
1/ To help our computers without our permission, somehow? or
2/ To help Ubuntu the OS (I know it is not a person) ... somehow?, or 
3/ Something I have not considered yet

Don't get me wrong ..I love Ubuntu ... and more importantly ...I hate Windows FINANCIAL DRAIN on everyone who owns one!
But this action ... appears ... to be more of a Windows type ploy!
In any case it was WITHOUT my/our consent!

Correct me if I am wrong!

---

### Post by markackerman8@gmail.com on 2020-01-14
To end in a positive note ...
...

Ubuntu thanks for listening ... at least!

Always Trying to help[, Mark

---

