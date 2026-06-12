---
title: "Broken Software Center [Ubuntu 14.04 LTS]"
date: 2015-06-06
forum: General Help
---

### Post by fossilman on 2015-06-06
I was trying to install a program named DOSBox and somehow in middle of the installation it started to show an error message that the Software Center was having problems, after reading a lot of pages here at the Forums most recommend to use the command "sudo apt-get -f install" I did and I get the following message:

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gcc-4.8-base:i386 libexpat1:i386 libffi6:i386 libgcrypt11:i386
  libgnutls26:i386 libgpg-error0:i386 libp11-kit0:i386 libsqlite3-0:i386
  libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386 p7zip wine-gecko2.24
  wine-gecko2.24:i386 wine-mono4.5.2 wine-staging-amd64 winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.9-base:i386
The following NEW packages will be installed:
  gcc-4.9-base:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
20 not fully installed or removed.
Need to get 0 B/14.9 kB of archives.
After this operation, 218 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 483909 files and directories currently installed.)
Preparing to unpack .../gcc-4.9-base_4.9.1-0ubuntu1_i386.deb ...
Unpacking gcc-4.9-base:i386 (4.9.1-0ubuntu1) ...
dpkg: error overwrite shared '/usr/share/doc/gcc-4.9-base/changelog.Debian.gz',  which is different from other instances of package gcc-4.9-base:i386
Errors were encountered while processing:
 /var/cache/apt/archives/gcc-4.9-base_4.9.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) processing archive /var/cache/apt/archives/gcc-4.9-base_4.9.1-0ubuntu1_i386.deb (--unpack):

```
 
Any suggestions?

---

### Post by TheFu on 2015-06-07
Sorry, the 2nd post of stuff has too many intermixed output messages to be deciphered. It can be removed.
Looks like there was an issue with the command entered being run in the background, then you switched to a root session for some reason.

Please edit that post with output from 1 command, and please show the exact command used.

---

