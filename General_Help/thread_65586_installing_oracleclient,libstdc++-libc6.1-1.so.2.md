---
title: "installing oracleclient,libstdc++-libc6.1-1.so.2"
date: 2005-09-14
forum: General Help
---

### Post by meckatzermichel on 2005-09-14
hello,
i tried to install the oracle client. when starting the installer i get the following:
error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or director

where can i get those libraries ? didn't find them with synaptic.

thanks in advance
meckatzermichel

---

### Post by cristyde on 2005-09-14
Hi, I have the exact same problem in Breeze 5.10 trying to install Oracle 9i 9.2.0.4
Help appreciated!

---

### Post by cristyde on 2005-09-14
I installed libstdc++2.10-glibc2.2 (available w/ Synaptic) and now I have the file /usr/lib/libstdc++-libc6.2-2.so.3, which I linked to the required libstdc++-libc6.1-1.so.2, but now I get the following message:

Error occurred during initialization of VM
Unable to load native library: /tmp/OraInstall2005-09-14_01-16-11PM/jre/lib/i386/libjava.so: symbol __libc_wait, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

 ](*,)

---

### Post by cristyde on 2005-09-14
I have the runInstaller running!!
I did this: 
Install gcc-295, libxp6 and libc6
I have no other gcc installed

cd /usr/bin
ln -s gcc-2.95 gcc

Applied patch 3006854 (although it says it's only for RHAS 3.0)

unzip p3006854_9204_LINUX.zip (search in MetaLink)
cd 3006854/
chmod 700 rhel3_pre_install.sh
./rhel3_pre_install.sh

And voila!, the installer starts (I haven't installed anything yet)

 \\:D/

---

### Post by pacer on 2005-09-19
Hello, 
Please tell me which installation pakage have you downloaded from oracle to install oraclient on Ubuntu.

The one that i have, tells me ...
Starting Oracle Universal Installer...

Checking installer requirements...

Checking operating system version: must be redhat-3, SuSE-9, redhat-4, UnitedLinux-1.0, asianux-1 or asianux-2
                                      Failed <<<<

How can i install it on Ubuntu?

---

### Post by cristyde on 2005-09-19
[QUOTE=pacer]Hello, 
Please tell me which installation pakage have you downloaded from oracle to install oraclient on Ubuntu.

The one that i have, tells me ...
Starting Oracle Universal Installer...

Checking installer requirements...

Checking operating system version: must be redhat-3, SuSE-9, redhat-4, UnitedLinux-1.0, asianux-1 or asianux-2
                                      Failed <<<<

How can i install it on Ubuntu?[/QUOTE]
 You need to trick Oracle Universal Installer to make it think it's running on another (ie. supported) distro. You can do this:

[FONT=Courier New]echo "Red Hat Enterprise Linux AS release 3 (Taroon)" > /etc/redhat-release[/FONT]

I'ts a dirty trick, I know, but works.
Then try again.

---

### Post by zaqxsw on 2005-09-30
Have you tried the Oracle Instant Client ?  It's precompiled and works well on Redhat, no installtion is required.

---

### Post by cristyde on 2005-10-01
Yes, but we're installing a server or other product.  ;-)

---

### Post by cristyde on 2005-10-01
Sorry I didn't read the subject. I was installing a server, but Pacer was installing a client, so your help is welcome.

---

### Post by meckatzermichel on 2005-12-27
i managed to install the oracle client on ubuntu hoary hedgehog in the meantime. unfortunately was not documenting it. (damn, i know, but...it was little bit like crisytide did.)
i will try again on breezy badger and post. but it can take a little time....(holidays at the moment ;-)
@cristyde:
i need only the client there because i like to use the enterprise manager

best regards
meckatzermichel

---

### Post by danran on 2006-04-07
Hi, i'm having problems with the converted rpm to deb alien conversion/install.  This is what I get:

dwozniak@sevilla:~/Desktop$ alien -div oracle-instantclient-10.1.0.3-3.nosrc.rpm
Must run as root to convert to deb format (or you may use fakeroot).
dwozniak@sevilla:~/Desktop$ sudo alien -div oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{SUMMARY} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{POSTIN} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{NAME} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{POSTUN} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{PREUN} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{RELEASE} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{PREFIXES} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{COPYRIGHT} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{DESCRIPTION} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{ARCH} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{VERSION} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qp --queryformat %{PREIN} oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qcp oracle-instantclient-10.1.0.3-3.nosrc.rpm
        rpm -qpi oracle-instantclient-10.1.0.3-3.nosrc.rpm
        LANG=C rpm -qpl oracle-instantclient-10.1.0.3-3.nosrc.rpm
        mkdir oracle-instantclient-10.1.0.3
        chmod 755 oracle-instantclient-10.1.0.3
        rpm2cpio oracle-instantclient-10.1.0.3-3.nosrc.rpm | (cd oracle-instantclient-10.1.0.3; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
        find oracle-instantclient-10.1.0.3 -type d -perm 755 -print0 | xargs --no-run-if-empty -0 chmod 755
        chown 0:0 oracle-instantclient-10.1.0.3/oracle-instantclient-config
        chmod 664 oracle-instantclient-10.1.0.3/oracle-instantclient-config
        chown 0:0 oracle-instantclient-10.1.0.3/oracle-instantclient.spec
        chmod 664 oracle-instantclient-10.1.0.3/oracle-instantclient.spec
        mkdir oracle-instantclient-10.1.0.3/debian
        hostname -f
        822-date
        hostname -f
        822-date
        chmod 755 oracle-instantclient-10.1.0.3/debian/rules
        debian/rules binary 2>&1
        dpkg --no-force-overwrite -i oracle-instantclient_10.1.0.3-4_i386.deb
        find oracle-instantclient-10.1.0.3 -type d -exec chmod 755 {} ;
        rm -rf oracle-instantclient-10.1.0.3

When I search for it I get nothing:
dwozniak@sevilla:~/Desktop$ sudo find / -name "*oracle-instantclient*" -print
/var/lib/dpkg/info/oracle-instantclient.md5sums
/var/lib/dpkg/info/oracle-instantclient.list
/usr/share/doc/oracle-instantclient
/home/dwozniak/Desktop/oracle-instantclient-10.1.0.3-3.nosrc.rpm
/oracle-instantclient-config
/oracle-instantclient.spec


I don't know if this help but here this:
dwozniak@sevilla:/var/lib/dpkg/info$ cat oracle-instantclient.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/oracle-instantclient
/usr/share/doc/oracle-instantclient/copyright
/usr/share/doc/oracle-instantclient/changelog.Debian.gz
/oracle-instantclient-config
/oracle-instantclient.spec

BTW, i'm planning on using the 10g client to connect to the db.  On a different system, i'm using 9i.  Will there be any compatibility issues with the 10g client?

Thanks.
--Dan W.

---

