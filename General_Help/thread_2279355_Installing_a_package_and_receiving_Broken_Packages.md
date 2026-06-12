---
title: "Installing a package and receiving Broken Packages Error ; Note- there are no broken"
date: 2015-05-22
forum: General Help
---

### Post by anthony_colombo on 2015-05-22
Hello.
 So I am trying to install mono-devel , mono-complete and have run  sudo apt-get build-dep mono-devel /mono-complete,  then ran sudo apt-get install -y mono-devel/mono-complete, and have received the following errors.

 Note- I first ran the advice from [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa) about fixiing and removing broken packages.

```
SYSTEM INFO

vagrant@precise64:~$ lsb_release -a        
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
```


```
vagrant@precise64:~$ sudo apt-get update
[sudo] password for vagrant: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [63.5 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [81.4 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B] 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [25.2 kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,333 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [272 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [63.5 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release [63.5 kB]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8,875 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [104 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3,681 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [260 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [205 kB]       
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [104 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,840 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [3,433 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [117 kB]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,152 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [524 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [11.8 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [280 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [513 kB] 
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [11.8 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [281 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [5,851 B]    
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [25.9 kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [6,256 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [29.7 kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,245 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [6,285 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [29.7 kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,249 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 3,154 kB in 22s (141 kB/s)                                             
Reading package lists... Done
```


For finding any held packages,  I have none  shown :


```
agrant@precise64:~$ sudo apt-get -u dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```.


for fixing any broken packages I have none  ; shown


```
vagrant@precise64:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


```
vagrant@precise64:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
Done
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

```
vagrant@precise64:~$ sudo apt-get install mono-complete
[sudo] password for vagrant: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
```


```
The following packages have unmet dependencies:
 mono-complete : Depends: mono-runtime (= 3.2.8+dfsg-4ubuntu1.1) but 4.0.1-0xamarin5 is to be installed
                 Depends: mono-runtime-sgen (= 3.2.8+dfsg-4ubuntu1.1) but 4.0.1-0xamarin5 is to be installed
                 Depends: libmono-2.0-1 (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: mono-utils (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: mono-devel (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: mono-mcs (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: mono-2.0-gac (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: mono-4.0-gac (= 3.2.8+dfsg-4ubuntu1.1) but 4.0.1-0xamarin5 is to be installed
                 Depends: mono-2.0-service (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: monodoc-manual (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
                 Depends: libmono-cil-dev (= 3.2.8+dfsg-4ubuntu1.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```


My issue is that it appears that I do NOT have any broken packages.

 I have rebooted my machine, and received the same error.

Advice?
I am stuck.

---

### Post by QIII on 2015-05-22
Please use code tags.  It makes your post much easier to read.

To use code tags you may either:

1.  Click the # symbol in the toolbar above the text entry box and place your cursor between them before pasting -or- paste, highlight the pasted text and then click the # symbol.

2.  Type [noparse]```
[/noparse] then either type or paste your text and then type [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by QDR06VV9 on 2015-05-22
Maybe this will help [https://zxtech.wordpress.com/2014/12/28/how-to-install-mono-on-ubuntu/](https://zxtech.wordpress.com/2014/12/28/how-to-install-mono-on-ubuntu/)
Regards

---

### Post by anthony_colombo on 2015-05-22
I solved this issue by using aptitude, and not apt-get.  

sudo aptitude install mono-devel  worked for me


however, it now looks like 3.2.8 is the latest version'?   Should mono version 3.12.1 be installed?

vagrant@precise64:~$ sudo apt-get install mono-complete
[sudo] password for vagrant: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mono-complete is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vagrant@precise64:~$ mono --version
Mono JIT compiler version 3.2.8 (tarball Mon May  5 23:06:49 UTC 2014)
Copyright (C) 2002-2014 Novell, Inc, Xamarin Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none
	Misc:          softdebug 
	LLVM:          supported, not enabled.
	GC:            sgen

---

### Post by mc4man on 2015-05-22
Edit - I guess you resolved, so moot - 

Your issue is that you've, at some point,  installed or have in cache  some mono packages from I believe some outside  Debian repos. They are at version - 4.0.1-0xamarin5
Ex.'s posted are - 
mono-runtime & mono-4.0-gac
You should probably remove them specifically & any other packages from whatever > Debian. Then you may proceed with Ubuntu based ones.
(or get whatever you are trying to install from Debian in versions compatible with what you have now....

Edit2 - they came from here - [http://origin-download.mono-project.com/repo/debian/dists/wheezy/main/binary-amd64/Packages](http://origin-download.mono-project.com/repo/debian/dists/wheezy/main/binary-amd64/Packages), probably following this at some point previously - [http://www.mono-project.com/docs/getting-started/install/linux/#debian-ubuntu-and-derivatives](http://www.mono-project.com/docs/getting-started/install/linux/#debian-ubuntu-and-derivatives)

---

