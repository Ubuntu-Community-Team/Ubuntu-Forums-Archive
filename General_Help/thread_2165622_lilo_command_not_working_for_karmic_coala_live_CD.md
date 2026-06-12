---
title: "lilo command not working for karmic coala live CD"
date: 2013-08-05
forum: General Help
---

### Post by bha2 on 2013-08-05
Hi,
Actually this belongs to the following thread [http://ubuntuforums.org/showthread.php?t=1009707](http://ubuntuforums.org/showthread.php?t=1009707)
But as that thread is closed I have started this as a new thread.
Mine is a MSI Laptop and I have the ubuntu karmic coala (9.10) version.
My OSs are kind of gone through a lot and I am starting afresh.......So I am going for ms-sys & lilo to fix my MBR with Ubuntu Live CD option...
Here are the errors I get for ms-sys & lilo

```
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ cd ms-sys
ubuntu@ubuntu:~/ms-sys$ make
mkdir -p dep
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/br.d src/br.c > dep/br.d
mkdir -p obj
mkdir -p bin
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/br.o src/br.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/fat12.d src/fat12.c > dep/fat12.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/fat12.o src/fat12.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/fat16.d src/fat16.c > dep/fat16.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/fat16.o src/fat16.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/fat16fd.d src/fat16fd.c > dep/fat16fd.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/fat16fd.o src/fat16fd.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/fat32.d src/fat32.c > dep/fat32.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/fat32.o src/fat32.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/fat32fd.d src/fat32fd.c > dep/fat32fd.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/fat32fd.o src/fat32fd.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/fat32nt.d src/fat32nt.c > dep/fat32nt.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/fat32nt.o src/fat32nt.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/file.d src/file.c > dep/file.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/file.o src/file.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/identify.d src/identify.c > dep/identify.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/identify.o src/identify.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/main.d src/main.c > dep/main.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/main.o src/main.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/nls.d src/nls.c > dep/nls.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/nls.o src/nls.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/ntfs.d src/ntfs.c > dep/ntfs.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/ntfs.o src/ntfs.c
cc -MM -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -MT dep/partition_info.d src/partition_info.c > dep/partition_info.d
cc -O2 -ansi -pedantic -Wall -c -I inc -D PACKAGE=\"ms-sys\" -D LOCALEDIR=\"/usr/local/share/locale\" -idirafter include-fallback -D_FILE_OFFSET_BITS=64  -o obj/partition_info.o src/partition_info.c
cc -o bin/ms-sys obj/br.o obj/fat12.o obj/fat16.o obj/fat16fd.o obj/fat32.o obj/fat32fd.o obj/fat32nt.o obj/file.o obj/identify.o obj/main.o obj/nls.o obj/ntfs.o obj/partition_info.o 

mkdir -p mo
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 127
ubuntu@ubuntu:~/ms-sys$ make install
install -D -m 755 bin/ms-sys /usr/local/bin/ms-sys
install: cannot create regular file `/usr/local/bin/ms-sys': Permission denied
make: *** [/usr/local/bin/ms-sys] Error 1
ubuntu@ubuntu:~/ms-sys$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbab21f87

 Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19430   115113757+   f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686    7  HPFS/NTFS
/dev/sda6           10199       15297    40957686    7  HPFS/NTFS
/dev/sda7           15298       18944    29294496   83  Linux
/dev/sda8           18945       19430     3903763+  82  Linux swap / Solaris

ubuntu@ubuntu:~/ms-sys$ sudo ms-sys -m /dev/sda1
sudo: ms-sys: command not found
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
 mbr
Suggested packages:
lilo-doc
The following NEW packages will be installed:
lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main mbr 1.1.10-2
Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main lilo 1:22.8-8ubuntu1
Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda1 mbr
sudo: lilo: command not found
ubuntu@ubuntu:~$ 
```
 
 
 
What can I do?I cannot use net while in Ubuntu because my mobile broadband connection provider's ubuntu package on installation is showing errors.whatever I am trying to install it shows errors...help
Thnx
bha

---

### Post by bapoumba on 2013-08-05
May I ask why you still have such an old release ?
The repos are not on ubuntu.com but on old-releases.ubuntu.com. You have to change your sources.list accordingly.

---

### Post by deadflowr on 2013-08-05
> **bapoumba said:**
> May I ask why you still have such an old release ?
The repos are not on ubuntu.com but on old-releases.ubuntu.com. You have to change your sources.list accordingly.

Here, Here!
This command will help convert the source.list from the archives to the old-release archives
```
sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```

Double check it and make sure the lines say old-release and not something like us.old-release or something similar.
Then run an update and see what happens next.

---

### Post by bapoumba on 2013-08-05
Neat thanks :)
Edit: backup the sources.list file before modifying it.

---

### Post by bha2 on 2013-08-09
oops...that didn't work either..i think
I am not a ubuntu maestro.....so i would appreciate if u will me what exactly to do

here is the scenario
[FONT=&quot]
ubuntu@ubuntu:~$ sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
ubuntu@ubuntu:~$ sudo apt-get install lilo[/FONT][FONT=&quot]
Reading[/FONT] package lists... Done
[FONT=&quot][/FONT]  Building dependency tree       

[FONT=&quot][/FONT]  Reading state information... Done

[FONT=&quot][/FONT]  Package lilo is not available, but is referred to by another package.

[FONT=&quot][/FONT]  This may mean that the package is missing, has been obsoleted, or

[FONT=&quot][/FONT]  is only available from another source

[FONT=&quot][/FONT]  E: Package lilo has no installation candidate

[FONT=&quot][/FONT]  ubuntu@ubuntu:~$ 

[FONT=&quot][/FONT]

---

### Post by deadflowr on 2013-08-09
Did you run 
```
sudo apt-get update
```
After changing the source.list?
If not, then you're still pulling from the obsolete package archive and not the old-release archive.
The update command is also helpful for fixing any problems that might have occurred when you changed the list.
(Sometimes repos like the partner repos need to be commented(#) out in the list.)
Post the output of the update if any problems occur.
Please use code tags(# symbol in the reply box toolbar) in the reply.

---

### Post by bha2 on 2013-08-11
Hmm.. here is the output
#  ubuntu@ubuntu:~$ sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

  ubuntu@ubuntu:~$ sudo apt-get update

  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic Release.gpg
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/main Translation-en_US
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/restricted Translation-en_US
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security Release.gpg
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/main Translation-en_US
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/restricted Translation-en_US
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates Release.gpg
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/main Translation-en_US
  Could not resolve 'old-releases.ubuntu.com'
  Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not resolve 'old-releases.ubuntu.com'
  Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
  Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
  Reading package lists... Done
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://old-releases.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://old-releases.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://old-releases.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://old-releases.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://old-releases.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'old-releases.ubuntu.com'
  W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://old-releases.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'old-releases.ubuntu.com'
  W: Some index files failed to download, they have been ignored, or old ones used instead.
  ubuntu@ubuntu:~$

---

### Post by mc4man on 2013-08-11
Are you connected to the internet?, your sudo apt-get update results suggest you're not.

Ex. when connected from live cd - 
> ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) saucy/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) saucy/restricted Translation-en_US
Get:1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic Release.gpg [189B] 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/restricted Translation-en_US
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security Release.gpg [198B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/restricted Translation-en_US
Get:3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates Release.gpg [198B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/restricted Translation-en_US
Get:4 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic Release [65.9kB]
Get:5 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security Release [51.3kB]
Get:6 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates Release [51.3kB]
Get:7 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/main Packages [1,353kB]
Get:8 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/restricted Packages [7,971B]
Get:9 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/main Sources [640kB]
Get:10 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic/restricted Sources [3,270B]
Get:11 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/main Packages [231kB]
Get:12 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/restricted Packages [14B]
Get:13 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/main Sources [128kB]
Get:14 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-security/restricted Sources [14B]
Get:15 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/main Packages [346kB]
Get:16 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/restricted Packages [1,631B]
Get:17 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/main Sources [166kB]
Get:18 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) karmic-updates/restricted Sources [878B]
Fetched 3,046kB in 3s (859kB/s)                      
Reading package lists... Done
Though not sure what value there is to installing lilo in a live session

---

### Post by bha2 on 2013-08-12
Hi,
I mentioned in my first post that i cannot connect to net while in ubuntu....So what should i do to start from scratch?download the latest version of ubuntu and using that go for live session and then try installing lilo?

---

### Post by deadflowr on 2013-08-12
Until you get your internet conncetion up and working, it won't matter what version you run.
You need a connection to get to the repos.

You can however, download packages from here
[http://packages.ubuntu.com/search?keywords=lilo](http://packages.ubuntu.com/search?keywords=lilo)

Though, you would need to upgrade to one of the supported versions listed.

Alternatively, sites like sourceforge might have lilo packages which will run on karmic.

---

