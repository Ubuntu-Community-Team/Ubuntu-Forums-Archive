---
title: "[HOWTO] Install Asterisk 13 in Ubuntu Saucy"
date: 2014-12-06
forum: General Help
---

### Post by s-stefanov on 2014-12-06
Steps should be pretty similar for other releases as well:
```

sudo apt-get install -y build-essential wget aptitude libjansson4 gdb strace uuid-dev sqlite3 libsqlite3-dev checkinstall libssl-dev libssl-doc ncurses-dev

cd /tmp

wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-13-current.tar.gz

tar zxvf asterisk-13-current.tar.gz

cd asterisk-13.0.1/
./configure

# Select components you want to install

make menuselect
make
sudo checkinstall


# At the final step the package fails to install due to a conflict with libspeex (probably fixed in 14.04). Libspeex uses crapy version conflict checking and 13.0.1 although much newer than what is necessary doesn't go through.

dpkg: regarding .../asterisk_13.0.1-1_amd64.deb containing asterisk:
libspeex1:amd64 conflicts with asterisk (<= 1:1.4.18.1~dfsg-1)
asterisk (version 13.0.1-1) is to be installed.

To overcome this during checkinstall select option 3:

This package will be built according to these values: 

0 -  Maintainer: [ root@VM ]
1 -  Summary: [ asterisk ]
2 -  Name:    [ asterisk ]
**3 -  Version: [ 13.0.1 ]**

Put something newer than the latest in the repo so that it doesn't get overwritten, e.g. 1:1.13.0.1

Output should look like this now:

0 -  Maintainer: [ root@VM ]
1 -  Summary: [ asterisk ]
2 -  Name:    [ asterisk ]
[B]3 -  Version: [ 1:1.13.0.1 ]
[/B]
N.B. This step might not be necessary on newer Ubuntu releases.

# Generate config files in /etc/asterisk

sudo make samples

# Generate daemon startup files in /etc/rc.*

sudo make config

# Remove crap from your system (be careful with this step not to break other apps):

sudo apt-get purge build-essential aptitude gdb strace uuid-dev libsqlite3-dev libjansson-dev libltdl-dev libtinfo-dev libncurses5-dev libserf1 libsvn1 libtinfo-dev libtool libxml2-dev subversion libxml2-dev libsqlite3-dev libjansson-dev uuid-dev libssl-dev uuid-dev
 
# Make sure libjansson4 doesn't get purged by autoclean/autoremove:

sudo sh -c "echo libjansson4 hold | dpkg --set-selections"

# Otherwise you'll get the following error message:

$ sudo asterisk -rvvv
asterisk: error while loading shared libraries: libjansson.so.4: cannot open shared object file: No such file or directory

Guide compiled thanks to:

http://www.ipcomms.net/sample-device-configurations/41-asterisk/181-install-asterisk-13-on-ubuntu-debian
https://github.com/abourget/asterisk-docker/blob/master/Dockerfile

``` 

That's it, you should have a running Asterisk 13 now. Couldn't manage to compile pjsip so I need to investigate. Stuck with chan_sip for now but it gets the job done.

Version 1: Initial draft
Version 2: Few extra dependencies added

---

### Post by nerdtron on 2014-12-06
Looks like you are compiling from source.
People here would like to help you but your system is no longer supported. Saucy Salamander is already End-of-life. Please upgrade to Ubuntu 14.04 LTS which is supported until April 2019.
Ubuntu Releases: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

BTW. your first step won't work on Saucy Salamander since the repository is already closed for that release.

---

### Post by s-stefanov on 2014-12-06
Actually, I don't need help (at least for now). What I'm writing is a guide, should be applicable to 14.04 as well.

Gotta go back home before upgrading my server because the 14.04 installer crapped my laptop when tried to upgrade from 13.10. I'm never doing the mistake of trying to upgrade Ubuntu ever again - so far 3 out of 3 massive failures starting from 10.04 till 14.04 going through all stable releases.

---

