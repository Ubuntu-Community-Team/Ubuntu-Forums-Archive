---
title: "Apt-get problem"
date: 2014-12-09
forum: General Help
---

### Post by CkDGTAT on 2014-12-09
Hi,

I am currently unable to install anything. How am I supposed to solve the problem?

Thank you


```
sudo apt-get install gpartedReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gparted : Depends: libatkmm-1.6-1 (>= 2.22.1) but it is not going to be installed
           Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
           Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
           Depends: libglibmm-2.4-1c2a (>= 2.30.0) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.14.0) but it is not going to be installed
           Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not going to be installed
           Depends: libpangomm-1.4-1 (>= 2.27.1) but it is not going to be installed
           Depends: libparted0debian1 (>= 2.2-1) but it is not going to be installed
           Depends: libsigc++-2.0-0c2a (>= 2.0.2) but it is not going to be installed
           Depends: libstdc++6 (>= 4.6) but it is not going to be installed
 libc6 : Depends: libgcc1 but it is not going to be installed
         Depends: tzdata but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by CkDGTAT on 2014-12-09
```
 sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apt-utils coreutils debconf debconf-i18n dpkg libacl1 libapt-inst1.4 libapt-pkg4.12 libattr1 libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl perl-base tar tzdata xz-utils zlib1g
Suggested packages:
  debconf-doc debconf-utils whiptail dialog gnome-utils libterm-readline-gnu-perl libgtk2-perl libnet-ldap-perl libqtgui4-perl libqtcore4-perl apt bzip2 ncompress xz-lzma
The following NEW packages will be installed:
  apt-utils coreutils debconf debconf-i18n dpkg libacl1 libapt-inst1.4 libapt-pkg4.12 libattr1 libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl perl-base tar tzdata xz-utils zlib1g
0 upgraded, 24 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,291 kB of archives.
After this operation, 29.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_i386.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_i386.deb (--unpack):
 pre-dependency problem - not installing libgcc1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_i386.deb
E: Internal Error, No file name for libc6
W: Could not perform immediate configuration on 'multiarch-support:i386'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by matt_symes on 2014-12-09
Hi

> : Cannot get debconf version. Is debconf installed? 
debconf: apt-extracttemplates failed: No such file or directory 
dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_i386.deb containing libgcc1, pre-dependency problem:  libgcc1 pre-depends on multiarch-support   
multiarch-support is unpacked, but has never been configured

The above error messages seem to be the root cause of the problem.

To give us a starting point, can you post the output of these commands from the terminal.

```
apt-cache policy debconf multiarch-support
```

```
dpkg -l debconf multiarch-support
```

And if we could look at your sources files.

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

