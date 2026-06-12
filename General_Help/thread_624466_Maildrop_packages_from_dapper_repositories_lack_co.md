---
title: "Maildrop packages from dapper repositories lack courier-authlib support"
date: 2007-11-27
forum: General Help
---

### Post by tylerk4 on 2007-11-27
Hello,

I've been working on setting up an e-mail server using postfix, courier-imap and maildrop.  Users for virtual domains are stored in a mysql database as per the usual postfixadmin structure.

Courier authenticates clients who connect to their mailboxes correctly.  Postfix correctly processes incoming mail.  However, maildrop is unable to figure out how to deliver messages due to the fact that the version I'm able to install from the dapper repositories doesn't have Courier Authentication Library support.  This means that as far as maildrop is concerned, users do not exist because it isn't able to access the mysql table containing such information.

Is there a repository that has a maildrop package that contains courier-authlib/mysql support?  I'd really like to try to avoid compiling maildrop from source, as that's already given me headaches.

Some system information below, including my current sources.list, on the off chance it is helpful.

```
root@bellend:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

root@bellend:~# uname -a
Linux bellend 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux

root@bellend:~# cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

---

### Post by tylerk4 on 2007-11-27
Bump, since this has apparently been buried.

---

### Post by volksman on 2007-11-30
courier-authmysql is the package name under 6.06

---

### Post by pot_roast on 2007-11-30
> **volksman said:**
> courier-authmysql is the package name under 6.06

But that package specifically says to not use it unless you're using it with sqwebmail.

We're back at square 1. :|

---

### Post by nickjqw on 2007-12-13
I'm working through the same issue, so far no real luck.  I've even tried recompiling the source dpkg, but I get this when trying to use maildrop:

```
*** glibc detected *** free(): invalid pointer: 0x08e0100b ***
maildrop: signal 0x06

```

I've tried compiling source for the 1.8.x and 2.x versions as well, but these don't seem to compile in mysql support (needs courier for that).

I'm in a rush, but I'll post back here if I ever get it working.

BTW, here is the ldd output on the old server that works (mandrake) and the new one (dapper).

OLD:
```

ldd /usr/local/bin/maildrop
        libfam.so.0 => /usr/lib/libfam.so.0 (0x40028000)
        libgdbm.so.3 => /usr/lib/libgdbm.so.3 (0x40031000)
        libmysqlclient.so.12 => /usr/lib/libmysqlclient.so.12 (0x40037000)
        libz.so.1 => /usr/lib/libz.so.1 (0x4006e000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0x4007f000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x400ad000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x400c0000)
        libm.so.6 => /lib/tls/libm.so.6 (0x40192000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x401b5000)
        libc.so.6 => /lib/tls/libc.so.6 (0x401be000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x40000000)

```

NEW: 
```

ldd /usr/local/bin/maildrop 
        libgdbm.so.3 => /usr/lib/libgdbm.so.3 (0x00d2b000)
        libmysqlclient.so.12 => /usr/lib/libmysqlclient.so.12 (0x00531000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00e4d000)
        libcrypt.so.1 => /lib/tls/libcrypt.so.1 (0x005c8000)
        libnsl.so.1 => /lib/tls/libnsl.so.1 (0x0062a000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00111000)
        libm.so.6 => /lib/tls/libm.so.6 (0x007b7000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x006c4000)
        libc.so.6 => /lib/tls/libc.so.6 (0x001e6000)
        /lib/ld-linux.so.2 (0x008dc000)

```

Of course the Ubuntu provided package doesn't include mysql support at all.  The only difference in libraries between the two is libfam, doubt that's an issue...

---

### Post by nickjqw on 2007-12-14
After about 4 hours of recompiling from souce, testing, messing with build options and starting over again, I've got maildrop + mysql working on Ubuntu 6.06 (Dapper).

Major credit is due to the people over at SysCP.  Their howto for Debian Sarge is nearly what we needed, unfortunately their how-to was pretty hard to find.  Here is the current [link]("http://syscp.org/wiki/docs/Installation/extensionmaildrop")

**Overview**

Here is what I did:

1.  Get courier source package (yeah, I know the package description says to use the standalone maildrop unless you are using sqwebmail package, but hey, it works.
2.  Review and manually apply patches fro SysCP to the source
3.  Compile (copiles all of couier even though we only want maildrop)
4.  Install courier-base package
5.  Install newly built courier-maildrop package


**Details**


*Get the source:
```
cd /usr/local/src
sudo apt-get source courier-maildrop
```

*Update files main.C and debian/rules (files attached):
```
# (make sure you are still in /usr/local/src)
# Also, edit the maildrop_debian_rules.patch file to include what users should be allowed to use maildrop, via the line:
# --enable-trusted-users="mail postfix root dspam"
patch -p0 <  maildrop_main_C.patch
patch -p0 < maildrop_debian_rules.patch
```

*Build the packages (took 15 minutes on our VPS):
```
sudo apt-get source courier-maildrop -b
```

*Install packages
```
sudo apt-get install courier-base
sudo dpkg -i courier-maildrop_0.47-13ubuntu5.1_i386.deb
```

*Enjoy!

Let me know if it works for you.  I'll also attach my package (courier-maildrop_0.47-13ubuntu5.1_i386.deb) built on 32bit x86.

---

