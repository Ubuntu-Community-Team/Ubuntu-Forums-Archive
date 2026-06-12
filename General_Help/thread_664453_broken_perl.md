---
title: "broken perl"
date: 2008-01-11
forum: General Help
---

### Post by ekayihura on 2008-01-11
Hi,

My perl is broken.
It started by a mistake I did by copying a file upon /usr/bin/perl
Then I tried reinstalling from package manager and failed then I purged with 
 sudo dpkg --purge perl.

The reinstall process stops like below

 sudo apt-get -f install perl
[sudo] password for eddy:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
Setting up perl (5.8.8-7ubuntu3.1) ...
/var/lib/dpkg/info/perl.postinst: 19: update-alternatives: not found
dpkg: error processing perl (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 perl
E: Sub-process /usr/bin/dpkg returned an error code (1)



Here is the situation 

sudo dpkg -s perl
Package: perl
Status: purge ok half-configured
Priority: standard
Section: perl
Installed-Size: 11444
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 5.8.8-7ubuntu3.1
Config-Version: 5.8.8-7ubuntu3.1
Replaces: perl-base (<< 5.8.8-1), perl-5.005 (<< 6), perl-5.6 (<< 6), perl-doc (<< 5.8.0-1), perl-modules (<< 5.8.1-1), libdigest-md5-perl, libmime-base64-perl, libtime-hires-perl, libstorable-perl
Provides: data-dumper, perl5, libdigest-md5-perl, libmime-base64-perl, libtime-hires-perl, libstorable-perl
Depends: perl-base (= 5.8.8-7ubuntu3.1), perl-modules (>= 5.8.8-7ubuntu3.1), libc6 (>= 2.6-1), libdb4.4, libgdbm3
Recommends: perl-doc
Suggests: libterm-readline-gnu-perl | libterm-readline-perl-perl
Conflicts: data-dumper, perl-5.004 (<< 6), perl-5.005 (<< 6), perl-5.6 (<< 6), perl-doc (<< 5.8.8-1), libdigest-md5-perl (<< 3.07-1), libmime-base64-perl (<< 3.07-1), libtime-hires-perl (<< 1.86-1), libstorable-perl (<< 2.15-1)
Description: Larry Wall's Practical Extraction and Report Language
 An interpreted scripting language, known among some as "Unix's Swiss
 Army Chainsaw".
 .
 Perl is optimised for scanning arbitrary text files and system
 administration.  It has built-in extended regular expression matching
 and replacement, a data-flow mechanism to improve security with
 setuid scripts and is extensible via modules that can interface to C
 libraries.
Original-Maintainer: Brendan O'Dea <bod@debian.org>

Is there any way I can have perl back on track.

Thanks

E.

---

### Post by geirha on 2008-01-11
dpkg-reconfigure is a perl script, so obviously that won't work if perl is broken. I think your best option is to boot the ubuntu CD, mount your / partition on /media/disk, if you have /usr on a seperate partition, mount it on /media/disk/usr.

Then, try installing perl from your ubuntu CD with: 
```
sudo aptitude download perl
sudo dpkg --root=/media/disk -i perl*.deb
```

when you uninstalled perl, it also took the debconf package with it (or so it appears), so try reinstalling that one too with the same procedure:
```
sudo aptitude download debconf
sudo dpkg --root=/media/disk -i debconf*.deb
```

---

### Post by ekayihura on 2008-01-11
Thanks Geirah,


> sudo aptitude download perl
downloaded ok from Internet correctly but the next step gave me this error


> sudo dpkg --root=/media/cdrom0 -i perl*.deb
dpkg: unable to access dpkg status area: No such file or directory

I thought this might give some more hints

 > mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=eddy)


Thanks

---

### Post by geirha on 2008-01-11
You need to boot from the CD, put the CD in, and restart the computer, from there try the procedure I proposed.

---

### Post by ekayihura on 2008-01-15
Thanks Geirah, it worked.
:-)

---

