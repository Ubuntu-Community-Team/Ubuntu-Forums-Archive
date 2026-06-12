---
title: "Recompiling cups-2.2.7 fail in Ubuntu 18.04"
date: 2018-09-28
forum: General Help
---

### Post by vansven on 2018-09-28
Hi,

I've applied a small patch to cups-2.2.7 (to solve the problem with "AuthInfoRequired negotiate" not working in Ubuntu 18.04 to be able to print through SMB-Kerberos) and would like to recompile the package. Everything seem to run smooth until the last run of "dpkg-buildpackage" where I expect to get my new deb-files that I would like to install. This is how I did:

# apt-get install dpkg-dev
# apt-get source cups
# cd cups-2.2.7
# patch -p1 < /tmp/the_patch_to_cups-2.2.7
# dpkg-buildpackage (it exits with  an error because I need to install some dependencies)
# apt-get install dh-apparmor dh-exec libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd-dev libfontconfig1-dev libfreetype6-dev libgnutls28-dev libijs-dev libldap2-dev libkrb5-dev libpam0g-dev libpaper-dev libsystemd-dev libtiff-dev libusb-1.0-0-dev po4a sharutil
# dpkg-buildpackage (it exits with  an error because I need to commit the patch)
# dpkg-source --commit (I choose to name it "cups-2.2.7-SMB-Kerberos")
# dpkg-buildpackage

The above last run of "dpkg-buildpackage" should result in building the deb-files I need but it ends like this:

[...]
Linking testsub...
cc -L../cgi-bin -L../cups -L../filter -L../ppdc -L../scheduler  -Wl,-Bsymbolic-functions -specs=/usr/share/dpkg/no-pie-link.specs  -Wl,-z,relro -Wl,-z,now -Wl,--as-needed  -fPIE -pie -Wall  -Wno-format-y2k -Wunused -fPIC -g -fstack-protector -Wno-unused-result  -Wsign-conversion -Wno-tautological-compare -Wno-format-truncation  -D_GNU_SOURCE -o testsub testsub.o ../cups/libcups.a \
        -lgnutls -lavahi-common -lavahi-client -lpthread -lm -lcrypt    -lz -lz -L/usr/lib/x86_64-linux-gnu/mit-krb5 -Wl,-Bsymbolic-functions  -Wl,-z,relro -lgssapi_krb5 -lkrb5 -lk5crypto -lcom_err
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/scheduler'
Making all in systemv...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/systemv'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/systemv'
Making all in conf...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/conf'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/conf'
Making all in data...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/data'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/data'
Making all in desktop...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/desktop'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/desktop'
Making all in locale...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/locale'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/locale'
Making all in man...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/man'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/man'
Making all in doc...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/doc'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/doc'
Making all in examples...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/examples'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/examples'
Making all in templates...
make[3]: Entering directory '/root/system/cups/cups-2.2.7/templates'
make[3]: Nothing to be done for 'unittests'.
make[3]: Leaving directory '/root/system/cups/cups-2.2.7/templates'
echo Running CUPS test suite with defaults...
Running CUPS test suite with defaults...
cd test; ./run-stp-tests.sh 1 0 n n
Please run this as a normal user. Not supported when run as root.
Makefile:256: recipe for target 'check' failed
make[2]: *** [check] Error 1
make[2]: Leaving directory '/root/system/cups/cups-2.2.7'
debian/rules:201: recipe for target 'override_dh_auto_test' failed
make[1]: *** [override_dh_auto_test] Error 2
make[1]: Leaving directory '/root/system/cups/cups-2.2.7'
debian/rules:17: recipe for target 'build' failed
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build subprocess returned exit status 2
root@work:~/system/cups/cups-2.2.7#

When I then do "cd .." I can't see any .deb-files, it looks like this:

root@work:~/system/cups# ls -l
drwxr-xr-x 28 root root     4096 sep 27 17:09 cups-2.2.7
-rw-r--r--  1 root root   358988 sep 27 17:09 cups_2.2.7-1ubuntu2.1.debian.tar.xz
-rw-r--r--  1 root root     2764 sep 27 17:09 cups_2.2.7-1ubuntu2.1.dsc
-rw-r--r--  1 root root 10330296 mar 28  2018 cups_2.2.7.orig.tar.gz
-rw-r--r--  1 root root      872 mar 28  2018 cups_2.2.7.orig.tar.gz.asc
root@work:~/system/cups#

Sorry if I'm missing somethings obvious, maybe someone sees what I've done wrong?

Best regards, Van

---

### Post by vansven on 2018-09-28
Sorry, I did not notive the line "Please run this as a normal user. Not supported when run as root." at first.

Now it works when I run this as a normal user :)

---

### Post by ajgreeny on 2018-09-28
Great news and thanks for letting us know! 

Please now mark as SOLVED from the Thread Tools menu up-top if this is solved to your satisfaction. It is a great help to users searching the forum.

---

