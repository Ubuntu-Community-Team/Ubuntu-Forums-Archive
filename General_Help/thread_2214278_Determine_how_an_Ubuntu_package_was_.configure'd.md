---
title: "Determine how an Ubuntu package was ./configure'd"
date: 2014-03-31
forum: General Help
---

### Post by DigiAngel on 2014-03-31
Topic says it...I'd like to know the configure line that was used to create the squid package.  Looked at the contents in:

[http://packages.ubuntu.com/precise/squid](http://packages.ubuntu.com/precise/squid)

but I'm just not finding the ./configure line.  Any insight into this?  Thank you.

---

### Post by claracc on 2014-03-31
I don't understand very well what you are asking.

As far as I know ```
./configure
``` command running in a xterm, will check that you have all the software required (software package dependencies) in order to install a program (not a .deb), but a program which you are compiling from source. When you run ./configure you are using default settings for the program which are explained in README or INSTALL files.

Please see: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by steeldriver on 2014-03-31
maybe this thread from askubuntu will help? 

[Where can I find the configure options used to build a package?]("http://askubuntu.com/questions/48499/where-can-i-find-the-configure-options-used-to-build-a-package")

---

### Post by DigiAngel on 2014-03-31
Thanks...I think that's what I was looking for steel.

---

### Post by DigiAngel on 2014-04-01
This has been a surprisingly difficult thing to find....maybe I haven't been explaining well (didn't get an answer yet on launchpad.net either).   On 12.0.4...I do:

sudo apt-get install squid

This installs the squid package. How do I find out how that squid package was ./configure'd from source when it was compiled?  Thank you.

---

### Post by SeijiSensei on 2014-04-01
I was curious about this the other day and followed the suggestions in askubuntu thread cited above.  You actually have to drill down a ways from the [https://launchpad.net/ubuntu/+source/squid3](https://launchpad.net/ubuntu/+source/squid3) top URL.  If you scroll down that page, you'll see the various builds by Ubuntu release version.  I picked the top one for Trusty, and then clicked on the amd64 build to find the [build log](https://launchpad.net/ubuntu/+source/squid3/3.3.8-1ubuntu6/+build/5610519/+files/buildlog_ubuntu-trusty-amd64.squid3_3.3.8-1ubuntu6_UPLOADING.txt.gz).  It contains this configure command:
```
./configure --build=x86_64-linux-gnu  --prefix=/usr --includedir="\${prefix}/include" --mandir="\${prefix}/share/man" --infodir="\${prefix}/share/info" --sysconfdir=/etc --localstatedir=/var --libexecdir="\${prefix}/lib/squid3" --srcdir=. --disable-maintainer-mode --disable-dependency-tracking --disable-silent-rules   --datadir=/usr/share/squid3 --sysconfdir=/etc/squid3 --mandir=/usr/share/man --enable-inline --enable-async-io=8 --enable-storeio="ufs,aufs,diskd,rock" --enable-removal-policies="lru,heap" --enable-delay-pools --enable-cache-digests --enable-underscores --enable-icap-client --enable-follow-x-forwarded-for --enable-auth-basic="DB,fake,getpwnam,LDAP,MSNT,MSNT-multi-domain,NCSA,NIS,PAM,POP3,RADIUS,SASL,SMB" --enable-auth-digest="file,LDAP" --enable-auth-negotiate="kerberos,wrapper" --enable-auth-ntlm="fake,smb_lm" --enable-external-acl-helpers="file_userip,kerberos_ldap_group,LDAP_group,session,SQL_session,unix_group,wbinfo_group" --enable-url-rewrite-helpers="fake" --enable-eui --enable-esi --enable-icmp --enable-zph-qos --enable-ecap --disable-translation --with-swapdir=/var/spool/squid3 --with-logdir=/var/log/squid3 --with-pidfile=/var/run/squid3.pid --with-filedescriptors=65536 --with-large-files --with-default-user=proxy --enable-linux-netfilter 
```
I note that it doesn't include --enable-ssl.

---

### Post by DigiAngel on 2014-04-01
Thanks so much...that's exactly what I needed...and it's exactly what I'm going to add ;)  I'm just going to highjack the current executable squid.  Thank you!

---

### Post by SeijiSensei on 2014-04-02
If I were you, I'd follow the Squid developers' recommendation and [compile 3.4.4 from source]("http://www.squid-cache.org/Versions/v3/3.4/").  I just did that the other day on a CentOS gateway I manage because we would occasionally run afoul of [this bug](https://lists.ubuntu.com/archives/ubuntu-sponsors/2012-March/021680.html) which was fixed in later releases.  If you're thinking about proxying SSL connections with [SSLBump]("http://wiki.squid-cache.org/Features/SslBump"), then you want to use versions 3.3 or later so you can compile in support for transparent session hijacking ("--enable-ssl-crtd").

---

