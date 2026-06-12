---
title: "Update manager and Software center both  can't update, or &quot;repair package catalauge&quot;"
date: 2014-02-24
forum: General Help
---

### Post by z-6 on 2014-02-24
Hello all, I'm running Ubuntu 12.04, and are having trouble with the following:
When I open the Software Center it tells me "Items can not be installed or removed until package catalauge is repaired." When I accept the repairs it gives me this error:

  	 	 	 	   installArchives() failed: Error in function:  
 SystemError: E:Internal Error, No file name for libc6 
 E: Cannot get debconf version. Is debconf installed? 
 debconf: apt-extracttemplates failed: No such file or directory 
 E: Cannot get debconf version. Is debconf installed? 
 debconf: apt-extracttemplates failed: No such file or directory 
 E: Cannot get debconf version. Is debconf installed? 
 debconf: apt-extracttemplates failed: No such file or directory 
 E: Cannot get debconf version. Is debconf installed? 
 debconf: apt-extracttemplates failed: No such file or directory 
 dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb containing libgcc1, pre-dependency problem: 
  libgcc1 pre-depends on multiarch-support 
   multiarch-support is unpacked, but has never been configured. 
 dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb (--unpack): 
  pre-dependency problem - not installing libgcc1 
 No apport report written because MaxReports is reached already 
 Errors were encountered while processing: 
  /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb 
 Error in function:  
 SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
 dpkg: dependency problems prevent configuration of libc6: 
  libc6 depends on libgcc1; however: 
   Package libgcc1 is not installed. 
  libc6 depends on tzdata; however: 
   Package tzdata is not installed. 
 dpkg: error processing libc6 (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of multiarch-support: 
  multiarch-support depends on libc6 (>= 2.3.6-2); however: 
   Package libc6 is not configured yet. 
 dpkg: error processing multiarch-support (--configure): 
  dependency problems - leaving unconfigured


Upon agreeing to install updates in the Update MAnager I get the following:

The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.15-0ubuntu10.5) but 2.15-0ubuntu10.5 is installed
       Depends: libgcc1 but it is not installed
       Depends: tzdata but it is not installed


Could anyone help me out? I know very little about Ubuntu...

Much thanks, Zak.

---

### Post by zvacet on 2014-02-25
```
sudo dpkg --configure -a
```

---

### Post by z-6 on 2014-02-25
Thanks for the reply, I entered your command and this is what I got back:

dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
 multiarch-support

---

### Post by deadflowr on 2014-02-25
What happens if you run
```
sudo apt-get -f install
```
then run
```
sudo apt-get update && sudo apt-get dist-upgrade
```
?
Post any new problems that arise.

---

### Post by jeanjd63 on 2014-02-25
Hello

You can try  :
[B]sudo  dpkg  -i  --force-all  [COLOR=#000000]/var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb
[/COLOR][/B][COLOR=#000000]and then[/COLOR][B][COLOR=#000000]
sudo  apt-get  install  -f[/COLOR][/B]

---

### Post by z-6 on 2014-02-25
Deadflwr:
I entered the first command and got this:

```
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb (--unpack):
 pre-dependency problem - not installing libgcc1
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb
E: Internal Error, No file name for libc6
W: Could not perform immediate configuration on 'multiarch-support:amd64'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Then with the second I got:

```
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                               
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [97.6 kB]       
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg                           
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,782 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [363 kB]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources [452 kB]      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [90.9 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,443 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [387 kB] 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [95.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,641 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Sources [8,028 B]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Sources [105 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Sources [8,490 B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main amd64 Packages [752 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                    
Get:27 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [357 B] 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.2 kB]
Get:29 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [362 B] 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe amd64 Packages [236 kB]
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_CA               
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [14.5 kB]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [774 kB]
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [241 kB]
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.7 kB]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Sources  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_CA           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_CA           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en              
Fetched 3,824 kB in 8s (467 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libgcc1 but it is not installed
         Depends: tzdata but it is not installed
E: Unmet dependencies. Try using -f.
```




Jeanjd63,
First command:

```
dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 478 files and directories currently installed.)
Unpacking libgcc1 (from .../libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
dpkg: also configuring `multiarch-support' (required by `libgcc1')
dpkg: also configuring `libc6' (required by `libgcc1')
dpkg: also configuring `libc6' (required by `multiarch-support')
Setting up multiarch-support (2.15-0ubuntu10.5) ...
dpkg: libgcc1: dependency problems, but configuring anyway as you requested:
 libgcc1 depends on libc6 (>= 2.14).
Setting up libgcc1 (1:4.6.3-1ubuntu5) ...
dpkg: libc6: dependency problems, but configuring anyway as you requested:
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
Setting up libc6 (2.15-0ubuntu10.5) ...
dpkg: error processing libc6 (--install):
 package libc6 is already installed and configured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libc6
```

Then second commant:

```
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Selecting previously unselected package libbz2-1.0.
(Reading database ... 481 files and directories currently installed.)
Unpacking libbz2-1.0 (from .../libbz2-1.0_1.0.6-1_amd64.deb) ...
Setting up libbz2-1.0 (1.0.6-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package libselinux1.
(Reading database ... 487 files and directories currently installed.)
Unpacking libselinux1 (from .../libselinux1_2.1.0-4.1ubuntu1_amd64.deb) ...
Setting up libselinux1 (2.1.0-4.1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package zlib1g.
(Reading database ... 493 files and directories currently installed.)
Unpacking zlib1g (from .../zlib1g_1%3a1.2.3.4.dfsg-3ubuntu4_amd64.deb) ...
Setting up zlib1g (1:1.2.3.4.dfsg-3ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package tar.
(Reading database ... 498 files and directories currently installed.)
Unpacking tar (from .../tar_1.26-4ubuntu1_amd64.deb) ...
Setting up tar (1.26-4ubuntu1) ...
Selecting previously unselected package liblzma5.
(Reading database ... 515 files and directories currently installed.)
Unpacking liblzma5 (from .../liblzma5_5.1.1alpha+20110809-3_amd64.deb) ...
Setting up liblzma5 (5.1.1alpha+20110809-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package xz-utils.
(Reading database ... 523 files and directories currently installed.)
Unpacking xz-utils (from .../xz-utils_5.1.1alpha+20110809-3_amd64.deb) ...
Setting up xz-utils (5.1.1alpha+20110809-3) ...
Selecting previously unselected package libattr1.
(Reading database ... 561 files and directories currently installed.)
Unpacking libattr1 (from .../libattr1_1%3a2.4.46-5ubuntu1_amd64.deb) ...
Setting up libattr1 (1:2.4.46-5ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package libacl1.
(Reading database ... 566 files and directories currently installed.)
Unpacking libacl1 (from .../libacl1_2.2.51-5ubuntu1_amd64.deb) ...
Setting up libacl1 (2.2.51-5ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package coreutils.
(Reading database ... 571 files and directories currently installed.)
Unpacking coreutils (from .../coreutils_8.13-3ubuntu3.2_amd64.deb) ...
Selecting previously unselected package dpkg.
dpkg: regarding .../dpkg_1.16.1.2ubuntu7.2_amd64.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
  coreutils is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/dpkg_1.16.1.2ubuntu7.2_amd64.deb (--unpack):
 pre-dependency problem - not installing dpkg
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.16.1.2ubuntu7.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by jeanjd63 on 2014-02-26
You can try this :
sudo rm /var/lib/apt/lists/lock
[B][COLOR=#000000]sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo apt-get clean
sudo apt-get autoclean --purge
sudo apt-get dist-upgrade
sudo dpkg --force-all --configure -a
sudo apt-get -f install[/COLOR][/B]

---

### Post by z-6 on 2014-02-26
That fixed it, thank you!

---

### Post by Bucky Ball on 2014-02-26
Please mark thread as solved to help others. This will not close the thread so conversation may continue.

For future reference, please use [code] [ /code] tags when posting code. Neater, smaller and easier to read and manage. Thanks and good luck. ;)

I have added them to your last code here as an example.

---

