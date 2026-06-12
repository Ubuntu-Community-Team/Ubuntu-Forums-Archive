---
title: "Failed to download repository information"
date: 2013-03-11
forum: General Help
---

### Post by jakefish on 2013-03-11
I am getting this error when i try to update ??

W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/Release  Unable to find expected entry 'main/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Hope someone can help

John

---

### Post by ibjsb4 on 2013-03-11
This package is no longer available and needs to be removed from your sources list.

 [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by jakefish on 2013-03-15
i have removed them cheers, but i get this now ????

installArchives() failed: 
Extract templates from packages: 30%%
Extract templates from packages: 61%%
Extract templates from packages: 91%%
Extract templates from packages: 100%%
Preconfiguring packages ...


Extract templates from packages: 30%%
Extract templates from packages: 61%%
Extract templates from packages: 91%%
Extract templates from packages: 100%%
Preconfiguring packages ...


Extract templates from packages: 30%%
Extract templates from packages: 61%%
Extract templates from packages: 91%%
Extract templates from packages: 100%%
Preconfiguring packages ...


Extract templates from packages: 30%%
Extract templates from packages: 61%%
Extract templates from packages: 91%%
Extract templates from packages: 100%%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 10037 package 'libavcodec-extra-53:amd64':
 field name ``This' must be followed by colon
Error in function:

---

### Post by schragge on 2013-03-15
Open a terminal (**Ctrl**+**Alt**+**t**) and try ```

sudo apt-get clean
sudo dpkg --clear-avail
``` This should clear the last error message from dpkg, but *SystemError InstallArchives() failed* may still persist. What are you trying to install?

---

### Post by jakefish on 2013-03-27
jakefish@jakefish-System-Product-Name:~$ sudo apt-get clean
[sudo] password for jakefish: 
jakefish@jakefish-System-Product-Name:~$ sudo dpkg --clear-avail
jakefish@jakefish-System-Product-Name:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 icedtea-7-jre-jamvm : Depends: openjdk-7-jre-headless (= 7u15-2.3.7-0ubuntu1~12.10.1) but 7u15-2.3.7-0ubuntu1~12.10 is installed
 openjdk-7-jre-headless : Depends: openjdk-7-jre-lib (= 7u15-2.3.7-0ubuntu1~12.10) but 7u15-2.3.7-0ubuntu1~12.10.1 is installed
                          Recommends: icedtea-7-jre-jamvm (= 7u15-2.3.7-0ubuntu1~12.10) but 7u15-2.3.7-0ubuntu1~12.10.1 is installed
E: Unmet dependencies. Try using -f.
jakefish@jakefish-System-Product-Name:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openjdk-7-jre-headless
Suggested packages:
  sun-java6-fonts ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts
The following packages will be upgraded:
  openjdk-7-jre-headless
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 35.4 MB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main openjdk-7-jre-headless amd64 7u15-2.3.7-0ubuntu1~12.10.1 [35.4 MB]
Fetched 35.4 MB in 5s (7,042 kB/s)                 
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-dee-0.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-panelapplet-3.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdata1.7-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgail-gnome-module' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-argparse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnux-0.9-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-l10n-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmime2.4-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-vte-0.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'intltool-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsdvd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'medibuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagickcore3-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-media-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hyphen-en-us' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gnomeapplet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-themes-selected' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnomepanel2.24-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclass-accessor-perl' missing; assuming package has no files currently installed
(Reading database ... 281491 files and directories currently installed.)
Preparing to replace openjdk-7-jre-headless:amd64 7u15-2.3.7-0ubuntu1~12.10 (using .../openjdk-7-jre-headless_7u15-2.3.7-0ubuntu1~12.10.1_amd64.deb) ...
Unpacking replacement openjdk-7-jre-headless:amd64 ...
Setting up openjdk-7-jre-headless:amd64 (7u15-2.3.7-0ubuntu1~12.10.1) ...
update-binfmts: warning: current package is openjdk-7, but binary format already installed by openjdk-6
Setting up icedtea-7-jre-jamvm:amd64 (7u15-2.3.7-0ubuntu1~12.10.1) ...
jakefish@jakefish-System-Product-Name:~$

---

### Post by jakefish on 2013-04-05
I  am getting this too

E:Problem parsing dependency Depends, E:Error occurred while processing libdbusada0.2-dev (NewVersion2), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by schragge on 2013-04-05
Every time you get any dpkg error messages mentioning MergeList, the first thing to attempt is just to delete the package lists:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

```

---

### Post by jakefish on 2013-04-05
Thank you  I tried that and it helped a little, but when I ran software update I got this

installArchives() failed: Segmentation fault (core dumped)
Segmentation fault (core dumped)
Segmentation fault (core dumped)
Segmentation fault (core dumped)
(Reading database ... 
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-dee-0.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-panelapplet-3.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdata1.7-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgail-gnome-module' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-argparse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnux-0.9-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-l10n-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmime2.4-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-vte-0.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'intltool-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsdvd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'medibuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagickcore3-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-media-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hyphen-en-us' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gnomeapplet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-themes-selected' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnomepanel2.24-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclass-accessor-perl' missing; assuming package has no files currently installed
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 308503 files and directories currently installed.)
Preparing to replace libavutil-extra-51:amd64 6:0.8.5ubuntu0.12.10.1 (using .../libavutil-extra-51_6%%3a0.8.6ubuntu0.12.10.1_amd64.deb) ...
Unpacking replacement libavutil-extra-51:amd64 ...
Error in function: 
Setting up libavutil-extra-51:amd64 (6:0.8.6ubuntu0.12.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by schragge on 2013-04-06
Looks like you've cut off some info: dpkg error messages are usually more verbose than just *Error in function:* Anyway, last time this happened, you did
```

sudo apt-get clean
sudo dpkg --clear-avail

``` So try it once again.

---

### Post by jakefish on 2013-04-09
thanks again, tried that and i get this

Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 29016 package 'odbcinst1debian2:amd64':
 `Depends' field, reference to `libc6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
jakefish@jakefish-System-Product-Name:~$ 


john

---

### Post by jakefish on 2013-04-17
i get this when i use synaptics manager ???

Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 29016 package 'odbcinst1debian2:amd64':
 `Depends' field, reference to `libc6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 29016 package 'odbcinst1debian2:amd64':
 `Depends' field, reference to `libc6': version contains ` '

---

### Post by schragge on 2013-04-17
That's a nasty error. Try
```
dpkg -s odbcinst1debian2:amd64
``` and post the output back here. If that gives you the same error, try
```
sed -n 29014,+5p /var/lib/dpkg/status
```
I'd like to look at the line in */var/lib/dpkg/status* dpkg is nagging about.

---

### Post by jakefish on 2013-04-19
cheers

jakefish@jakefish-System-Product-Name:~$ dpkg -s odbcinst1debian2:amd64
dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 29016 package 'odbcinst1debian2:amd64':
 `Depends' field, reference to `libc6': version contains ` '
jakefish@jakefish-System-Product-Name:~$

---

### Post by jakefish on 2013-04-19
jakefish@jakefish-System-Product-Name:~$ sed -n 29014,+5p /var/lib/dpkg/status
Version: 2.2.14p2-uubuntu4
Replaces: unixodbc (<< 2.1.1-2)
Depends: libc6 (>= 2.14i, libltdl7 (>= 2.4.2), odbcinst
Pre-Depends: multiarch-support
Breaks: libiodbc2, libmyodbc (<< 5.1.6-2), odbc-postgresql (<< 1z09.00.0310-1.1), tdsodbc (<< 0.82-8)
Conflicts: odbcinst1, odbcinst1debian1
jakefish@jakefish-System-Product-Name:~$ 


thank you for your help

John

---

### Post by jakefish on 2013-04-19
tried synaptic again and got

Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 29016 package 'odbcinst1debian2:amd64':
 `Depends' field, reference to `libc6': version contains ` '
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 29016 package 'odbcinst1debian2:amd64':
 `Depends' field, reference to `libc6': version contains ` '


how can i show you what is on 29016 ???

---

### Post by schragge on 2013-04-20
You've already did:
```
Depends: libc6 (>= 2.14[COLOR=#FF0000]i[/COLOR], libltdl7 (>= 2.4.2), odbcinst
``` That [COLOR=#FF0000]i[/COLOR] there is what's causing the problem. To replace it with a closing parenthesis, run
```
sudo sed -i '29016s/14i/14)/' /var/lib/dpkg/status
```
The version *2.2.14p2-[COLOR=#FF0000]u[/COLOR]ubuntu4* is also wrong. It should be *2.2.14p2-[COLOR=#ff0000]5[/COLOR]ubuntu4*. Let's fix it as well: 
```
sudo sed -i 29014s/uu/5u/ /var/lib/dpkg/status
```
After that, re-install the package, just in case:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install odbcinst1debian2:amd64

```
Looks like you are running a 32-bit system, so I'm wondering why you have some 64-bit packages installed at all? Could you please post the output of the following commands?
```
uname -a
```
```
lsb_release -a
```

---

### Post by jakefish on 2013-04-21
This is the error I got

thanks

jakefish@jakefish-System-Product-Name:~$ sudo apt-get --reinstall install odbcinst1debian2:amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  odbcinst1debian2
1 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
Need to get 51.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main odbcinst1debian2 amd64 2.2.14p2-5ubuntu4 [51.8 kB]
Fetched 51.8 kB in 0s (147 kB/s)            
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 29042 package 'odbcinst1debian2:i386':
 `Depends' field, reference to `libltdl7':
 `>' is obsolete, use `>=' or `>>' instead
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 29042 package 'odbcinst1debian2:i386':
 `Depends' field, reference to `libltdl7':
 version value starts with non-alphanumeric, suggest adding a space
dpkg: error: parsing file '/var/lib/dpkg/status' near line 29042 package 'odbcinst1debian2:i386':
 `Depends' field, reference to `libltdl7': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by jakefish on 2013-04-21
jakefish@jakefish-System-Product-Name:~$ uname -a
Linux jakefish-System-Product-Name 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jakefish on 2013-04-21
lsb_release -ajakefish@jakefish-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

---

### Post by jakefish on 2013-04-21
Thank you for your continued support

John

---

### Post by schragge on 2013-04-21
Well, I was wrong: you are on a 64-bit architecture. And now we've got the same problem with *odbcinst1debian2:i386* Let's try the same approach: post the output of
```
sed -n 29040,+5p /var/lib/dpkg/status
```

---

### Post by jakefish on 2013-04-22
jakefish@jakefish-System-Product-Name:~$ sed -n 29040,+5p /var/lib/dpkg/status
Config-Version: 2.2.14p2-5ubuntu4
Replaces: unixodbc (<< 2.1.1-2)
Depends: libc6 (>= 2.4), libltdl7 (>} 2.4.2), odbcinst
Pre-Depends: multiarch-support
Breaks: libiodbc2, libmyodbc (<< 5.1.6-2), odbc-postgresql (<< 1:09.00.0310-1.q), tdsodbc (<< 0.82-8)
Conflicts: odbcinst1, odbcinst1debian1

---

### Post by schragge on 2013-04-22
Okay, now let's fix it: ```
sudo sed -i 29042s/}/=/ /var/lib/dpkg/status
``` After that, try again
```
sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install odbcinst1debian2

```

---

### Post by jakefish on 2013-04-22
this happened ??

jakefish@jakefish-System-Product-Name:~$ sudo sed -i 29042s/}/=/ /var/lib/dpkg/status
[sudo] password for jakefish: 
jakefish@jakefish-System-Product-Name:~$ sudo apt-get clean
jakefish@jakefish-System-Product-Name:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg    
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [180 kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [227 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [10.6 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [4,804 B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages [181 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages [225 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages [10.8 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages [4,841 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en [108 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en [95.0 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Fetched 1,098 kB in 4s (259 kB/s)
Reading package lists... Done
jakefish@jakefish-System-Product-Name:~$ sudo apt-get --reinstall install odbcinst1debian2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  odbcinst1debian2
1 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
Need to get 51.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main odbcinst1debian2 amd64 2.2.14p2-5ubuntu4 [51.8 kB]
Fetched 51.8 kB in 0s (388 kB/s)            
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-dee-0.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-panelapplet-3.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdata1.7-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgail-gnome-module' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-argparse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnux-0.9-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-l10n-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmime2.4-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-vte-0.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'intltool-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsdvd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'medibuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagickcore3-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-media-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hyphen-en-us' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gnomeapplet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-themes-selected' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnomepanel2.24-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclass-accessor-perl' missing; assuming package has no files currently installed
(Reading database ... 308503 files and directories currently installed.)
Preparing to replace odbcinst1debian2:amd64 2.2.14p2-5ubuntu4 (using .../odbcinst1debian2_2.2.14p2-5ubuntu4_amd64.deb) ...
Unpacking replacement odbcinst1debian2:amd64 ...
Setting up odbcinst1debian2:amd64 (2.2.14p2-5ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jakefish@jakefish-System-Product-Name:~$

---

### Post by schragge on 2013-04-23
At least, you'll be able to use synaptic again and upgrade packages as usual. Still, I'd recommend to purge or reinstall all the packages dpkg's warning about.

These probably should be reinstalled:
```
sudo apt-get --reinstall install lib{io-string,class-accessor}-perl intltool-debian lsdvd hyphen-en-us
```

These are obsolete and definitely should be removed:
```

sudo dpkg -P gir1.2-{dee-0.5,panelapplet-3.0,vte-0.0} libg{data1.7,mime2.4,nomepanel2.24}-cil gnome-{media-common,themes-selected}
sudo dpkg -P lib{gail-gnome-module,magickcore3-extra,{nux-0.9,reoffice-l10n}-common} python-{argparse,gnomeapplet} linux-headers-2.6.38-8{,-generic}

```
As to the rest, make your own judgment. I'd probably remove *linux-headers-3.5.0-17{,-generic}* and reinstall *medibuntu-keyring*

---

### Post by jakefish on 2013-04-23
jakefish@jakefish-System-Product-Name:~$ sudo dpkg -P gir1.2-{dee-0.5,panelapplet-3.0,vte-0.0} libg{data1.7,mime2.4,nomepanel2.24}-cil gnome-{media-common,themes-selected}
dpkg: warning: files list file for package 'gir1.2-dee-0.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-panelapplet-3.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdata1.7-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgail-gnome-module' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-argparse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnux-0.9-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-l10n-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmime2.4-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-vte-0.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'medibuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagickcore3-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-media-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gnomeapplet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-themes-selected' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnomepanel2.24-cil' missing; assuming package has no files currently installed
(Reading database ... 308538 files and directories currently installed.)
Removing gir1.2-dee-0.5 ...
Removing gir1.2-panelapplet-3.0 ...
Removing gir1.2-vte-0.0 ...
Removing libgdata1.7-cil ...
Removing libgmime2.4-cil ...
Removing libgnomepanel2.24-cil ...
dpkg: dependency problems prevent removal of gnome-media-common:
 libgnome-media0 depends on gnome-media-common (>= 2.32).
 libgnome-media0 depends on gnome-media-common (<< 2.33).
 libgnome-media0 depends on gnome-media-common (>= 2.32).
 libgnome-media0 depends on gnome-media-common (<< 2.33).


dpkg: error processing gnome-media-common (--purge):
 dependency problems - not removing
Removing gnome-themes-selected ...
Errors were encountered while processing:
 gnome-media-common

---

### Post by jakefish on 2013-04-23
jakefish@jakefish-System-Product-Name:~$ sudo dpkg -P lib{gail-gnome-module,magickcore3-extra,{nux-0.9,reoffice-l10n}-common} python-{argparse,gnomeapplet} linux-headers-2.6.38-8{,-generic}
dpkg: warning: files list file for package 'libgail-gnome-module' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-argparse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnux-0.9-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-l10n-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-2.6.38-8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-17-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'medibuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagickcore3-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-media-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gnomeapplet' missing; assuming package has no files currently installed
(Reading database ... 308538 files and directories currently installed.)
Removing libgail-gnome-module ...
Removing libmagickcore3-extra ...
dpkg: dependency problems prevent removal of libnux-0.9-common:
 libnux-0.9-0 depends on libnux-0.9-common (= 0.9.48-0ubuntu1.1).


dpkg: error processing libnux-0.9-common (--purge):
 dependency problems - not removing
Removing libreoffice-l10n-common ...
Removing python-argparse ...
Removing python-gnomeapplet ...
Removing linux-headers-2.6.38-8-generic ...
Removing linux-headers-2.6.38-8 ...
Errors were encountered while processing:
 libnux-0.9-common

---

### Post by jakefish on 2013-04-23
Thank you schragge for your help so far, its almost there.


john

---

### Post by schragge on 2013-04-23
Okay. Let's try it this way
```
sudo apt-get purge libnux-0.9-{0,common} libgnome-media0 gnome-media-common
```

---

### Post by jakefish on 2013-04-24
jakefish@jakefish-System-Product-Name:~$ sudo apt-get update
[sudo] password for jakefish: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Reading package lists... Done
jakefish@jakefish-System-Product-Name:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jakefish@jakefish-System-Product-Name:~$ 


it would seem everything is fine, thanks for your patience

John

---

