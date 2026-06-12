---
title: "acpi-support: dependency problems"
date: 2008-03-01
forum: General Help
---

### Post by banjopikker on 2008-03-01
How do I fix this? I get this error whenever I install or uninstall software or do updates.


E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: xubuntu-desktop: dependency problems - leaving unconfigured

---

### Post by banjopikker on 2008-03-05
No ideas??

---

### Post by pointone on 2008-03-05
There should be more to the error message than you're reporting here. Run "sudo apt-get update" and "sudo apt-get -f install" from the terminal and paste the output here in full.

---

### Post by banjopikker on 2008-03-05
ran sudo apt-get update . returned
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

Ran .. sudo apt-get -f install....returned with

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmtp5 libmagick9 libmono-security1.0-cil libgstreamer0.8-0 libgksu1.2-1
  libmono0 pkg-config vorbis-tools libmono-sharpzip0.84-cil libgksuui1.0-1
  libgstreamer-gconf0.8-0 libflac++5c2 gstreamer0.8-gnomevfs libfame-0.9 fftw3
  libmono-system-web1.0-cil cli-common libgtksourceview1.0-0
  libmono-corlib1.0-cil libpvm3 kdemultimedia-kio-plugins metacity-common
  mysql-common libsoup2.2-8 libkcddb1 libgpod1 libcurl3-gnutls mono-common
  libmysqlclient15off ruby1.8 libkleopatra1 kdebase-kio-plugins ruby
  libmono-system1.0-cil kdebase-bin mono-gac libgtksourceview-common
  libmono-data-tds1.0-cil mono-jit libtunepimp5 libifp4
  libmono-system-data1.0-cil kdesktop libmetacity0 liblo0 libgda2-3
  libgstreamer-plugins0.8-0 libgpgme11 rosegarden-data libraptor1
  libtotem-plparser1 liblrdf0 libruby1.8 libgda2-common binfmt-support
  libgnome-desktop-2 libmono-cairo1.0-cil libnjb5 libgdl-1-0 libofa0
  libgdiplus gstreamer0.8-cdparanoia libgdl-1-common libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu6) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 xubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pointone on 2008-03-05
Post the output of "sudo tail -20 /var/log/acpid" after running "sudo dpkg --reconfigure acpid".

Also post the output of running "sudo /etc/init.d/acpid restart".

---

### Post by banjopikker on 2008-03-06
I ran   sudo dpkg --reconfigure acpid   it returned.....dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
roger@roger-desktop:~$ sudo dpkg -reconfigure acpid
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

Ran  sudo /etc/init.d/acpid restart...    returned  .... * Stopping ACPI services...                                             [ OK ] 

 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...

---

### Post by pointone on 2008-03-06
Oops! I should've said "sudo dpkg-reconfigure acpid".

---

### Post by banjopikker on 2008-03-06
ran...sudo dpkg-reconfigure acpid.. it returned

/usr/sbin/dpkg-reconfigure: acpid is broken or not fully installed

---

### Post by banjopikker on 2008-03-13
Just did a new update .I got this again.
E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: xubuntu-desktop: dependency problems - leaving unconfigured
 I don't know how to resolve this.

---

