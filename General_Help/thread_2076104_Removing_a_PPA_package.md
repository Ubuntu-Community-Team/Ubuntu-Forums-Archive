---
title: "Removing a PPA package"
date: 2012-10-25
forum: General Help
---

### Post by CCgirl6690 on 2012-10-25
HEllo .  i am trying to Remove Pidgin from my ubuntu 12 completely . i shouldnt have installed ppa on 12 i guess but i did . so im trying to remove it  and i found this command  ""sudo apt-get purge pidgin-ppa"" but then when i type in  ""ls /etc/apt/sources.list.d/pidgin*"" it still shows 2 files in there . so its not deleting them . and i cant remove them manually .move to trach" is disabled on my right click menu over those 2 files  so what can i do ? i need to reinstall the pidgin without PPA so it wont have bugs again..................  thank you..........................

---

### Post by pmlxuser on 2012-10-25
why not do a sudo rm /etc/apt/sources.list.d/pidgin* i do believe you know what you are doing thus the sudo...

---

### Post by NikTh on 2012-10-25
Hi , 

you can remove PPAs with several ways , but I prefer one. Via ppa-purge. 

ppa-purge is a script that will purge completely the ppa and the most important is that will downgrade the package(s) to the original state . All these automatically. 

```
sudo apt-get install ppa-purge
``` 
and then
```
sudo ppa-purge <ppa-name>
``` 

If you want to vanish the entries from sources.list.d/ then you can do it manually (probably these entries after the ppa-purge are useless, but remove the anyway). 
Via terminal 
```
sudo rm /etc/apt/sources.list.d/<ppa-entry>.list
``` 
or graphical via nautilus. 

**[COLOR=Red]Be careful[/COLOR]** when you use nautilus with admin privileges , you can destroy your system. 
```
gksudo nautilus /etc/apt/sources.list.d/
``` 
and remove the entries you want.

Thanks

---

### Post by CCgirl6690 on 2012-10-25
thank you . i think i didnt have ppa purge installed now i removed them .  thank again .     ____ one more question?   ...      @@@ how do i make sure im installing teh latest version Pidgin on ubuntu 12?  can i do it on ubunto software center?>???  thanksss

---

### Post by NikTh on 2012-10-25
> **CCgirl6690 said:**
> thank you . i think i didnt have ppa purge installed now i removed them .  thank again .     ____ one more question?   ...      @@@ how do i make sure im installing teh latest version Pidgin on ubuntu 12?  can i do it on ubunto software center?>???  thanksss

Ubuntu by default always install the latest version that is available in the Official repositories. 

An easy way to see what version is installed and what version(s) is(are) available is to open a terminal and give this command 

```
apt-cache policy <package name>
``` 
Example 
```
apt-cache policy pidgin
``` 

Thanks

---

### Post by CCgirl6690 on 2012-10-25
Thanks Nikth ...... i tried to reinstal pidgin on ubuntu software center . and now its giving me this error"" Package dependencies cannot be resolved""" ""This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."" details:The following packages have unmet dependencies:  pidgin: Depends: perlapi-5.14.2 but it is a virtual package""""  help me please

---

### Post by dino99 on 2012-10-25
so i suppose that you have installed also some other ppa(s), and they conflict; so purge them also and update again.

---

### Post by CCgirl6690 on 2012-10-25
how do i do that , dino

---

### Post by NikTh on 2012-10-25
> **CCgirl6690 said:**
> how do i do that

With the same way you purged the pidgin ppa. With ppa-purge program. 

Thanks

---

### Post by CCgirl6690 on 2012-10-25
but how do i know what and which to remove? tnaks

---

### Post by dino99 on 2012-10-25
> **CCgirl6690 said:**
> but how do i know what and which to remove? tnaks

i suppose that you might know what you have installed or not dont you ?

2 ways to follow, either:
- open sources.list    ```
   sudo gedit /etc/apt/sources.list 
```  

- or via synaptic:
sudo apt-get install synaptic
sudo synaptic

then check  Settings -> Repositories  about these ppas

then follow the ppa-purge howto

---

### Post by CCgirl6690 on 2012-10-25
ok so i typed the " sudo gedit /etc/apt/sources.list" and here is my list , now what am i looking @ ? and what should i do? thanks

[HTML]# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main[/HTML]

---

### Post by NikTh on 2012-10-25
Hi , 

give the results of this command please 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``` 

Thanks

---

### Post by CCgirl6690 on 2012-10-25
here 
[HTML]/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    41    deb http://security.ubuntu.com/ubuntu precise-security universe
    42    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    43    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu precise partner
    51    # deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main

/etc/apt/sources.list.d/tualatrix-ppa-precise.list

     1    deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main

/etc/apt/sources.list.d/webupd8team-java-precise.list

     1    deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
none@None:~$ 
[/HTML]

---

### Post by NikTh on 2012-10-25
Hi , 
please try 
```
sudo apt-get install --reinstall perl-base 
sudo apt-get install pidgin
sudo apt-get install -f
```and post back here  full results 

Thanks

---

### Post by CCgirl6690 on 2012-10-25
hi , it goes only this far 
[HTML]none@None:~$ sudo apt-get install --reinstall perl-base 
[sudo] password for none: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 19 not upgraded.
Need to get 1,472 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main perl-base i386 5.14.2-6ubuntu2.1 [1,472 kB]
Fetched 1,472 kB in 35s (41.8 kB/s)                                            
(Reading database ... 193415 files and directories currently installed.)
Preparing to replace perl-base 5.14.2-6ubuntu2.1 (using .../perl-base_5.14.2-6ubuntu2.1_i386.deb) ...
Unpacking replacement perl-base ...
Processing triggers for man-db ...
Setting up perl-base (5.14.2-6ubuntu2.1) ...
none@None:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pidgin : Depends: pidgin-data (< 1:2.10.3-z) but 1:2.10.6-0ubuntu1+pidgin1.12.04 is to be installed
          Recommends: pidgin-libnotify but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
none@None:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
none@None:~$ 
[/HTML]

---

### Post by CCgirl6690 on 2012-10-25
any quick Fix please?  i need pidgin
thanks

---

### Post by NikTh on 2012-10-26
Do you have the proposed-updates enabled ? 
Check 

```
gksudo software-properties-gtk
``` and at the opened window goto "Updates" and see if **Pre-Released updates (Precise-proposed)** are ticked. If yes then **UN-Tick** them.
Either way run in terminal
```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install pidgin
```give the results back here.

Thanks

---

### Post by CCgirl6690 on 2012-10-26
here
[HTML]none@None:~$ gksudo software-properties-gtk
none@None:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-locale-zh-hans kde-l10n-engb kde-l10n-zhcn language-pack-kde-en
  language-pack-kde-en-base language-pack-kde-zh-hans
  language-pack-kde-zh-hans-base language-pack-zh-hans
  language-pack-zh-hans-base
0 upgraded, 0 newly installed, 9 to remove and 19 not upgraded.
After this operation, 27.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 193414 files and directories currently installed.)
Removing firefox-locale-zh-hans ...
Removing kde-l10n-engb ...
Removing kde-l10n-zhcn ...
Removing language-pack-zh-hans-base ...
Removing language-pack-kde-en-base ...
Removing language-pack-kde-zh-hans-base ...
Removing language-pack-kde-en ...
Removing language-pack-kde-zh-hans ...
Removing language-pack-zh-hans ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
none@None:~$ sudo apt-get update
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease            
Ign http://us.archive.ubuntu.com precise InRelease                   
Ign http://us.archive.ubuntu.com precise-updates InRelease           
Ign http://us.archive.ubuntu.com precise-backports InRelease         
Ign http://extras.ubuntu.com precise InRelease                       
Hit http://ppa.launchpad.net precise Release.gpg                     
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]            
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]  
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:5 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:6 http://security.ubuntu.com precise-security/main Sources [50.6 kB]       
Get:7 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [14.5 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [184 kB] 
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:12 http://security.ubuntu.com precise-security/universe i386 Packages [48.7 kB]
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:13 http://us.archive.ubuntu.com precise-updates/main Sources [181 kB]      
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,357 B]
Get:15 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:16 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:17 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:18 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:19 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:20 http://us.archive.ubuntu.com precise-updates/universe Sources [60.7 kB] 
Get:21 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:22 http://us.archive.ubuntu.com precise-updates/main i386 Packages [423 kB]
Get:23 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:24 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [151 kB]
Get:25 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Get:26 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:27 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:28 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:29 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:30 http://us.archive.ubuntu.com precise-updates/main Translation-en [206 kB]
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:31 http://us.archive.ubuntu.com precise-updates/universe Translation-en [89.7 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 1,558 kB in 42s (36.4 kB/s)                                            
Reading package lists... Done
none@None:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apparmor apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 jockey-common
  jockey-gtk landscape-client-ui-install libapt-inst1.4 libapt-pkg4.12
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libldap-2.4-2
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libxcb-composite0 libxcb-dri2-0 libxcb-glx0
  libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1
  lsb-base lsb-release python-aptdaemon python-aptdaemon.gtk3widgets
  python-aptdaemon.pkcompat ubuntu-tweak unity-greeter update-notifier
  update-notifier-common xserver-xorg-input-wacom
40 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.0 MB of archives.
After this operation, 30.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ precise/main ubuntu-tweak all 0.8.1-1~precise1 [913 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-pkg4.12 i386 0.8.16~exp12ubuntu10.5 [943 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt i386 0.8.16~exp12ubuntu10.5 [1,089 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-inst1.4 i386 0.8.16~exp12ubuntu10.5 [103 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main lsb-base all 4.0-0ubuntu20.2 [10.4 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apparmor i386 2.7.102-0ubuntu3.2 [362 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libldap-2.4-2 i386 2.4.28-1.1ubuntu4.2 [186 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb1 i386 1.8.1-1ubuntu0.1 [48.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-composite0 i386 1.8.1-1ubuntu0.1 [5,650 B]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-dri2-0 i386 1.8.1-1ubuntu0.1 [7,902 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-glx0 i386 1.8.1-1ubuntu0.1 [28.4 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-randr0 i386 1.8.1-1ubuntu0.1 [15.6 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-render0 i386 1.8.1-1ubuntu0.1 [14.2 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-shape0 i386 1.8.1-1ubuntu0.1 [6,434 B]
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-shm0 i386 1.8.1-1ubuntu0.1 [5,682 B]
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-xv0 i386 1.8.1-1ubuntu0.1 [11.0 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier i386 0.119ubuntu8.6 [56.6 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier-common all 0.119ubuntu8.6 [222 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt-utils i386 0.8.16~exp12ubuntu10.5 [193 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main lsb-release all 4.0-0ubuntu20.2 [10.8 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt-transport-https i386 0.8.16~exp12ubuntu10.5 [16.3 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apport-symptoms all 0.16.1 [14.2 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwebkitgtk-3.0-0 i386 1.8.3-0ubuntu0.12.04.1 [7,312 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libjavascriptcoregtk-3.0-0 i386 1.8.3-0ubuntu0.12.04.1 [1,427 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwebkitgtk-3.0-common all 1.8.3-0ubuntu0.12.04.1 [756 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-webkit-3.0 i386 1.8.3-0ubuntu0.12.04.1 [66.7 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-javascriptcoregtk-3.0 i386 1.8.3-0ubuntu0.12.04.1 [12.4 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-gtk all 0.9.7-0ubuntu7.4 [9,112 B]
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-common all 0.9.7-0ubuntu7.4 [128 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main aptdaemon all 0.43+bzr805-0ubuntu5 [14.7 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-aptdaemon.pkcompat all 0.43+bzr805-0ubuntu5 [29.1 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-aptdaemon.gtk3widgets all 0.43+bzr805-0ubuntu5 [14.9 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-aptdaemon all 0.43+bzr805-0ubuntu5 [82.5 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main aptdaemon-data all 0.43+bzr805-0ubuntu5 [164 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main landscape-client-ui-install i386 12.05-0ubuntu1.12.04 [8,838 B]
Get:36 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwebkitgtk-1.0-common all 1.8.3-0ubuntu0.12.04.1 [756 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwebkitgtk-1.0-0 i386 1.8.3-0ubuntu0.12.04.1 [7,315 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libjavascriptcoregtk-1.0-0 i386 1.8.3-0ubuntu0.12.04.1 [1,427 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity-greeter i386 0.2.8-0ubuntu1.3 [86.2 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-wacom i386 1:0.14.0-0ubuntu2.1 [85.3 kB]
Fetched 24.0 MB in 3min 35s (111 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 190287 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.3 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.5_i386.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 190287 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.3 (using .../apt_0.8.16~exp12ubuntu10.5_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.5) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 190287 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.3 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.5_i386.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace lsb-base 4.0-0ubuntu20 (using .../lsb-base_4.0-0ubuntu20.2_all.deb) ...
Unpacking replacement lsb-base ...
Setting up lsb-base (4.0-0ubuntu20.2) ...
(Reading database ... 190287 files and directories currently installed.)
Preparing to replace apparmor 2.7.102-0ubuntu3.1 (using .../apparmor_2.7.102-0ubuntu3.2_i386.deb) ...
Unpacking replacement apparmor ...
Preparing to replace libldap-2.4-2 2.4.28-1.1ubuntu4.1 (using .../libldap-2.4-2_2.4.28-1.1ubuntu4.2_i386.deb) ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libxcb1 1.8.1-1 (using .../libxcb1_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb1 ...
Preparing to replace libxcb-composite0 1.8.1-1 (using .../libxcb-composite0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-composite0 ...
Preparing to replace libxcb-dri2-0 1.8.1-1 (using .../libxcb-dri2-0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-dri2-0 ...
Preparing to replace libxcb-glx0 1.8.1-1 (using .../libxcb-glx0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-glx0 ...
Preparing to replace libxcb-randr0 1.8.1-1 (using .../libxcb-randr0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-randr0 ...
Preparing to replace libxcb-render0 1.8.1-1 (using .../libxcb-render0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-render0 ...
Preparing to replace libxcb-shape0 1.8.1-1 (using .../libxcb-shape0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-shape0 ...
Preparing to replace libxcb-shm0 1.8.1-1 (using .../libxcb-shm0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-shm0 ...
Preparing to replace libxcb-xv0 1.8.1-1 (using .../libxcb-xv0_1.8.1-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxcb-xv0 ...
Preparing to replace update-notifier 0.119ubuntu8.5 (using .../update-notifier_0.119ubuntu8.6_i386.deb) ...
Unpacking replacement update-notifier ...
Preparing to replace update-notifier-common 0.119ubuntu8.5 (using .../update-notifier-common_0.119ubuntu8.6_all.deb) ...
Unpacking replacement update-notifier-common ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.3 (using .../apt-utils_0.8.16~exp12ubuntu10.5_i386.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace lsb-release 4.0-0ubuntu20 (using .../lsb-release_4.0-0ubuntu20.2_all.deb) ...
Unpacking replacement lsb-release ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.3 (using .../apt-transport-https_0.8.16~exp12ubuntu10.5_i386.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace apport-symptoms 0.16 (using .../apport-symptoms_0.16.1_all.deb) ...
Unpacking replacement apport-symptoms ...
Preparing to replace libwebkitgtk-3.0-0 1.8.1-0ubuntu0.12.04.1 (using .../libwebkitgtk-3.0-0_1.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libwebkitgtk-3.0-0 ...
Preparing to replace libjavascriptcoregtk-3.0-0 1.8.1-0ubuntu0.12.04.1 (using .../libjavascriptcoregtk-3.0-0_1.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libjavascriptcoregtk-3.0-0 ...
Preparing to replace libwebkitgtk-3.0-common 1.8.1-0ubuntu0.12.04.1 (using .../libwebkitgtk-3.0-common_1.8.3-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement libwebkitgtk-3.0-common ...
Preparing to replace gir1.2-webkit-3.0 1.8.1-0ubuntu0.12.04.1 (using .../gir1.2-webkit-3.0_1.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement gir1.2-webkit-3.0 ...
Preparing to replace gir1.2-javascriptcoregtk-3.0 1.8.1-0ubuntu0.12.04.1 (using .../gir1.2-javascriptcoregtk-3.0_1.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement gir1.2-javascriptcoregtk-3.0 ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.3 (using .../jockey-gtk_0.9.7-0ubuntu7.4_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.3 (using .../jockey-common_0.9.7-0ubuntu7.4_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace aptdaemon 0.43+bzr805-0ubuntu4 (using .../aptdaemon_0.43+bzr805-0ubuntu5_all.deb) ...
Unpacking replacement aptdaemon ...
Preparing to replace python-aptdaemon.pkcompat 0.43+bzr805-0ubuntu4 (using .../python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu5_all.deb) ...
Unpacking replacement python-aptdaemon.pkcompat ...
Preparing to replace python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu4 (using .../python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu5_all.deb) ...
Unpacking replacement python-aptdaemon.gtk3widgets ...
Preparing to replace python-aptdaemon 0.43+bzr805-0ubuntu4 (using .../python-aptdaemon_0.43+bzr805-0ubuntu5_all.deb) ...
Unpacking replacement python-aptdaemon ...
Preparing to replace aptdaemon-data 0.43+bzr805-0ubuntu4 (using .../aptdaemon-data_0.43+bzr805-0ubuntu5_all.deb) ...
Unpacking replacement aptdaemon-data ...
Preparing to replace landscape-client-ui-install 12.05-0ubuntu0.12.04 (using .../landscape-client-ui-install_12.05-0ubuntu1.12.04_i386.deb) ...
Unpacking replacement landscape-client-ui-install ...
Preparing to replace libwebkitgtk-1.0-common 1.8.1-0ubuntu0.12.04.1 (using .../libwebkitgtk-1.0-common_1.8.3-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement libwebkitgtk-1.0-common ...
Preparing to replace libwebkitgtk-1.0-0 1.8.1-0ubuntu0.12.04.1 (using .../libwebkitgtk-1.0-0_1.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libwebkitgtk-1.0-0 ...
Preparing to replace libjavascriptcoregtk-1.0-0 1.8.1-0ubuntu0.12.04.1 (using .../libjavascriptcoregtk-1.0-0_1.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libjavascriptcoregtk-1.0-0 ...
Preparing to replace ubuntu-tweak 0.8.0-1~precise1 (using .../ubuntu-tweak_0.8.1-1~precise1_all.deb) ...
Unpacking replacement ubuntu-tweak ...
Preparing to replace unity-greeter 0.2.8-0ubuntu1.2 (using .../unity-greeter_0.2.8-0ubuntu1.3_i386.deb) ...
Unpacking replacement unity-greeter ...
Preparing to replace xserver-xorg-input-wacom 1:0.14.0-0ubuntu2 (using .../xserver-xorg-input-wacom_1%3a0.14.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement xserver-xorg-input-wacom ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.5) ...
Setting up apparmor (2.7.102-0ubuntu3.2) ...
Installing new version of config file /etc/apparmor.d/abstractions/nameservice ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libldap-2.4-2 (2.4.28-1.1ubuntu4.2) ...
Setting up libxcb1 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-composite0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-dri2-0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-glx0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-randr0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-render0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-shape0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-shm0 (1.8.1-1ubuntu0.1) ...
Setting up libxcb-xv0 (1.8.1-1ubuntu0.1) ...
Setting up update-notifier-common (0.119ubuntu8.6) ...
Setting up update-notifier (0.119ubuntu8.6) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.5) ...
Setting up lsb-release (4.0-0ubuntu20.2) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.5) ...
Setting up apport-symptoms (0.16.1) ...
Setting up libjavascriptcoregtk-3.0-0 (1.8.3-0ubuntu0.12.04.1) ...
Setting up libwebkitgtk-3.0-common (1.8.3-0ubuntu0.12.04.1) ...
Setting up libwebkitgtk-3.0-0 (1.8.3-0ubuntu0.12.04.1) ...
Setting up gir1.2-javascriptcoregtk-3.0 (1.8.3-0ubuntu0.12.04.1) ...
Setting up gir1.2-webkit-3.0 (1.8.3-0ubuntu0.12.04.1) ...
Setting up jockey-common (0.9.7-0ubuntu7.4) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.4) ...
Setting up python-aptdaemon (0.43+bzr805-0ubuntu5) ...
Setting up aptdaemon (0.43+bzr805-0ubuntu5) ...
Setting up python-aptdaemon.pkcompat (0.43+bzr805-0ubuntu5) ...
Setting up aptdaemon-data (0.43+bzr805-0ubuntu5) ...
Setting up python-aptdaemon.gtk3widgets (0.43+bzr805-0ubuntu5) ...
Setting up landscape-client-ui-install (12.05-0ubuntu1.12.04) ...
Setting up libwebkitgtk-1.0-common (1.8.3-0ubuntu0.12.04.1) ...
Setting up libjavascriptcoregtk-1.0-0 (1.8.3-0ubuntu0.12.04.1) ...
Setting up libwebkitgtk-1.0-0 (1.8.3-0ubuntu0.12.04.1) ...
Setting up ubuntu-tweak (0.8.1-1~precise1) ...
Setting up unity-greeter (0.2.8-0ubuntu1.3) ...
Setting up xserver-xorg-input-wacom (1:0.14.0-0ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
none@None:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pidgin : Depends: pidgin-data (< 1:2.10.3-z) but 1:2.10.6-0ubuntu1+pidgin1.12.04 is to be installed
          Recommends: pidgin-libnotify but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
none@None:~$ [/HTML]

---

### Post by NikTh on 2012-10-26
Hi , 

please give the results ```
apt-cache policy pidgin pidgin-data
dpkg -l | grep -i pidgin
```Thanks

---

### Post by CCgirl6690 on 2012-10-26
[HTML]none@None:~$ apt-cache policy pidgin pidgin-data
pidgin:
  Installed: (none)
  Candidate: 1:2.10.3-0ubuntu1.1
  Version table:
     1:2.10.6-0ubuntu1+pidgin1.12.04 0
        100 /var/lib/dpkg/status
     1:2.10.3-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     1:2.10.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
pidgin-data:
  Installed: 1:2.10.6-0ubuntu1+pidgin1.12.04
  Candidate: 1:2.10.6-0ubuntu1+pidgin1.12.04
  Version table:
 *** 1:2.10.6-0ubuntu1+pidgin1.12.04 0
        100 /var/lib/dpkg/status
     1:2.10.3-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     1:2.10.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
none@None:~$ dpkg -l | grep -i pidgin
ii  indicator-status-provider-pidgin       0.6.0-0ubuntu1                          indicator-messages status provider for pidgin
ii  libpurple-bin                          1:2.10.6-0ubuntu1+pidgin1.12.04         multi-protocol instant messaging library - extra utilities
ii  libpurple0                             1:2.10.6-0ubuntu1+pidgin1.12.04         multi-protocol instant messaging library
ii  nautilus-sendto                        3.0.1-2ubuntu2                          integrates Evolution and Pidgin into the Nautilus file manager
rc  pidgin                                 1:2.10.6-0ubuntu1+pidgin1.12.04         graphical multi-protocol instant messaging client for X
ii  pidgin-data                            1:2.10.6-0ubuntu1+pidgin1.12.04         multi-protocol instant messaging client - data files
none@None:~$ 
[/HTML]

---

### Post by NikTh on 2012-10-26
Try
```
sudo apt-get remove libpurple-bin libpurple0 pidgin-data indicator-status-provider-pidgin
``````
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
sudo apt-get install pidgin
```

Thanks

---

### Post by CCgirl6690 on 2012-10-26
ugh
[HTML]none@None:~$ sudo apt-get remove libpurple-bin libpurple0 pidgin-data indicator-status-provider-pidgin
[sudo] password for none: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  indicator-status-provider-pidgin libpurple-bin libpurple0 pidgin-data
  telepathy-haze
0 upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
After this operation, 31.2 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 190290 files and directories currently installed.)
Removing indicator-status-provider-pidgin ...
Removing libpurple-bin ...
Removing telepathy-haze ...
Removing libpurple0 ...
Removing pidgin-data ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme ...
none@None:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
none@None:~$ sudo rm /var/lib/apt/lists/* -vf 
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources'
none@None:~$ sudo apt-get update 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://extras.ubuntu.com precise InRelease                       
Ign http://security.ubuntu.com precise-security InRelease            
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]           
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://us.archive.ubuntu.com precise InRelease                   
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:5 http://extras.ubuntu.com precise Release [11.9 kB]                       
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:7 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:8 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:9 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:10 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Get:11 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:12 http://extras.ubuntu.com precise/main Sources [7,480 B]                 
Get:13 http://security.ubuntu.com precise-security/main Sources [51.1 kB]      
Get:14 http://us.archive.ubuntu.com precise Release [49.6 kB]                  
Get:15 http://extras.ubuntu.com precise/main i386 Packages [9,796 B]           
Get:16 http://ppa.launchpad.net precise/main Sources [650 B]                   
Get:17 http://ppa.launchpad.net precise/main i386 Packages [656 B]             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:18 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:19 http://security.ubuntu.com precise-security/universe Sources [14.5 kB]  
Get:20 http://ppa.launchpad.net precise/main Sources [780 B]                   
Get:21 http://ppa.launchpad.net precise/main i386 Packages [1,978 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:22 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:23 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B]
Get:24 http://security.ubuntu.com precise-security/main i386 Packages [186 kB] 
Get:25 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:26 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Get:27 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:28 http://security.ubuntu.com precise-security/universe i386 Packages [48.7 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,357 B]
Get:30 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:31 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:32 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:33 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:34 http://security.ubuntu.com precise-security/main Translation-en [88.6 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:35 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]
Get:36 http://security.ubuntu.com precise-security/restricted Translation-en [978 B]
Get:37 http://security.ubuntu.com precise-security/universe Translation-en [30.3 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:38 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:39 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:40 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:41 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:42 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:43 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:44 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:45 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Get:46 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:47 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:48 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:49 http://us.archive.ubuntu.com precise-updates/main Sources [182 kB]      
Get:50 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Get:51 http://us.archive.ubuntu.com precise-updates/universe Sources [60.7 kB] 
Get:52 http://us.archive.ubuntu.com precise-updates/universe Sources [60.7 kB] 
Get:53 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:54 http://us.archive.ubuntu.com precise-updates/main i386 Packages [425 kB]
Get:55 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:56 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [151 kB]
Get:57 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Get:58 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:59 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:60 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:61 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:62 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:63 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:64 http://us.archive.ubuntu.com precise-backports/universe Sources [16.5 kB]
Get:65 http://us.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:66 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:67 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:68 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [14.9 kB]
Get:69 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:70 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:71 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:72 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:73 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Get:74 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:75 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:76 http://us.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:77 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB] 
Get:78 http://us.archive.ubuntu.com precise-updates/main Translation-en [206 kB]
Get:79 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [5,606 B]
Get:80 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [2,048 B]
Get:81 http://us.archive.ubuntu.com precise-updates/universe Translation-en [89.7 kB]
Get:82 http://us.archive.ubuntu.com precise-backports/main Translation-en [1,244 B]
Get:83 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [1,476 B]
Get:84 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:85 http://us.archive.ubuntu.com precise-backports/universe Translation-en [10.9 kB]
Fetched 18.4 MB in 2min 50s (107 kB/s)                                         
Reading package lists... Done
none@None:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pidgin : Depends: pidgin-data (< 1:2.10.3-z) but 1:2.10.6-0ubuntu1+pidgin1.12.04 is to be installed
          Recommends: pidgin-libnotify but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[/HTML]

---

### Post by NikTh on 2012-10-27
My results are 

```
apt-cache policy pidgin-data 
pidgin-data:
  Installed: (none)
  Candidate: **1:2.10.3-0ubuntu1.1**
  Version table:
     1:2.10.3-0ubuntu1.1 0
```I don't know where did you find this **1:2.10.6-0ubuntu1+pidgin1.12.04** , 
but I know. You found it here : [https://launchpad.net/~pidgin-developers/+archive/ppa/+build/3652768](https://launchpad.net/~pidgin-developers/+archive/ppa/+build/3652768)

So the only think I can thing is that you didn't remove properly the PPA . 

As a last effort (by me) , try to install again the PPA , update ```
sudo add-apt-repository ppa:pidgin-developers/ppa
sudo apt-get update
``` and then try to remove the PPA with the properly way 

```
sudo ppa-purge ppa:pidgin-developers/ppa
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install pidgin
```Thanks

---

### Post by CCgirl6690 on 2012-10-28
thank you very much nikith  , i dont knwo what was wrong but seems like it was installed already cuz still has my passwords saved and stuff . take a look yourself see what happened cuz when i tried to install it said its alleady newset version  , 
but again thank you very much for your help and time i appreciate this , so do you think i got rid of ppa now?  thanks
[HTML]sudnone@None:~$ sudo apt-get install pidgin
[sudo] password for none: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pidgin : Depends: pidgin-data (< 1:2.10.3-z) but 1:2.10.6-0ubuntu1+pidgin1.12.04 is to be installed
          Recommends: pidgin-libnotify but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
none@None:~$ sudo add-apt-repository ppa:pidgin-developers/ppa
You are about to add the following PPA to your system:
 This PPA contains packages of the current version of Pidgin for all versions of Ubuntu currently supported on the desktop. This allows you to stay current with Pidgin while using a stable release of Ubuntu.
 More info: https://launchpad.net/~pidgin-developers/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpe01RYy/secring.gpg' created
gpg: keyring `/tmp/tmpe01RYy/pubring.gpg' created
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpe01RYy/trustdb.gpg: trustdb created
gpg: key A1F196A8: public key "Launchpad PPA for Pidgin Developers" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
none@None:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                       
Ign http://ppa.launchpad.net precise InRelease                       
Ign http://ppa.launchpad.net precise InRelease                       
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Ign http://us.archive.ubuntu.com precise InRelease                             
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]            
Get:3 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://extras.ubuntu.com precise/main Sources                              
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]            
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:6 http://security.ubuntu.com precise-security/main Sources [51.1 kB]       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:7 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:8 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://ppa.launchpad.net precise Release                                   
Get:9 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Hit http://us.archive.ubuntu.com precise Release                               
Get:10 http://security.ubuntu.com precise-security/universe Sources [14.5 kB]  
Get:11 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:12 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B]
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [186 kB] 
Get:15 http://ppa.launchpad.net precise/main Sources [1,373 B]                 
Get:16 http://ppa.launchpad.net precise/main i386 Packages [3,139 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [48.7 kB]
Get:19 http://ppa.launchpad.net precise/main Sources [786 B]                   
Get:20 http://ppa.launchpad.net precise/main i386 Packages [1,966 B]           
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,357 B]
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:22 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:23 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:24 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:25 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources           
Ign http://extras.ubuntu.com precise/main Translation-en_US           
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Ign http://extras.ubuntu.com precise/main Translation-en              
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:26 http://us.archive.ubuntu.com precise-updates/main Sources [182 kB]      
Get:27 http://us.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Get:28 http://us.archive.ubuntu.com precise-updates/universe Sources [60.7 kB] 
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:30 http://us.archive.ubuntu.com precise-updates/main i386 Packages [425 kB]
Get:31 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:32 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [151 kB]
Get:33 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Get:34 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:35 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:36 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:37 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 1,299 kB in 21s (61.0 kB/s)                                            
Reading package lists... Done
none@None:~$ sudo ppa-purge ppa:pidgin-developers/ppa
Updating packages lists
PPA to be removed: pidgin-developers ppa
Package revert list generated:
 libpurple0/precise libpurple-bin/precise pidgin/precise pidgin-data/precise

Disabling pidgin-developers PPA from 
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '1:2.10.3-0ubuntu1.1' (Ubuntu:12.04/precise-updates [i386]) for 'libpurple0'
Selected version '1:2.10.3-0ubuntu1.1' (Ubuntu:12.04/precise-updates [all]) for 'libpurple-bin'
Selected version '1:2.10.3-0ubuntu1.1' (Ubuntu:12.04/precise-updates [i386]) for 'pidgin'
Selected version '1:2.10.3-0ubuntu1.1' (Ubuntu:12.04/precise-updates [all]) for 'pidgin-data' because of 'pidgin'
Selected version '1:2.10.3-0ubuntu1.1' (Ubuntu:12.04/precise-updates [all]) for 'pidgin-data'
The following extra packages will be installed:
  pidgin-libnotify
Suggested packages:
  tcl8.5 tk8.5
The following NEW packages will be installed:
  pidgin pidgin-libnotify
The following packages will be DOWNGRADED:
  libpurple-bin libpurple0 pidgin-data
0 upgraded, 2 newly installed, 3 downgraded, 0 to remove and 9 not upgraded.
Need to get 1,761 kB/3,575 kB of archives.
After this operation, 19.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpurple-bin all 1:2.10.3-0ubuntu1.1 [16.5 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpurple0 i386 1:2.10.3-0ubuntu1.1 [1,745 kB]
Fetched 1,761 kB in 9s (189 kB/s)                                              
dpkg: warning: downgrading libpurple-bin from 1:2.10.6-0ubuntu1+pidgin1.12.04 to 1:2.10.3-0ubuntu1.1.
(Reading database ... 
dpkg: warning: files list file for package `telepathy-haze' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpurple-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-status-provider-pidgin' missing, assuming package has no files currently installed.
(Reading database ... 191867 files and directories currently installed.)
Preparing to replace libpurple-bin 1:2.10.6-0ubuntu1+pidgin1.12.04 (using .../libpurple-bin_1%3a2.10.3-0ubuntu1.1_all.deb) ...
Unpacking replacement libpurple-bin ...
dpkg: warning: downgrading libpurple0 from 1:2.10.6-0ubuntu1+pidgin1.12.04 to 1:2.10.3-0ubuntu1.1.
Preparing to replace libpurple0 1:2.10.6-0ubuntu1+pidgin1.12.04 (using .../libpurple0_1%3a2.10.3-0ubuntu1.1_i386.deb) ...
Unpacking replacement libpurple0 ...
dpkg: warning: downgrading pidgin-data from 1:2.10.6-0ubuntu1+pidgin1.12.04 to 1:2.10.3-0ubuntu1.1.
Preparing to replace pidgin-data 1:2.10.6-0ubuntu1+pidgin1.12.04 (using .../pidgin-data_1%3a2.10.3-0ubuntu1.1_all.deb) ...
Unpacking replacement pidgin-data ...
Selecting previously unselected package pidgin.
Unpacking pidgin (from .../pidgin_1%3a2.10.3-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package pidgin-libnotify.
Unpacking pidgin-libnotify (from .../pidgin-libnotify_0.14-4ubuntu10_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for gconf2 ...
Setting up libpurple-bin (1:2.10.3-0ubuntu1.1) ...
Setting up libpurple0 (1:2.10.3-0ubuntu1.1) ...
Setting up pidgin-data (1:2.10.3-0ubuntu1.1) ...
Setting up pidgin (1:2.10.3-0ubuntu1.1) ...
Setting up pidgin-libnotify (0.14-4ubuntu10) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
PPA purged successfully
none@None:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apparmor firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  icedtea-7-jre-jamvm openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.4 MB of archives.
After this operation, 31.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? t
Abort.
none@None:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apparmor firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  icedtea-7-jre-jamvm openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.4 MB of archives.
After this operation, 31.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apparmor i386 2.7.102-0ubuntu3.4 [361 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe openjdk-7-jre i386 7u9-2.3.3-0ubuntu1~12.04.1 [225 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe icedtea-7-jre-jamvm i386 7u9-2.3.3-0ubuntu1~12.04.1 [538 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe openjdk-7-jre-headless i386 7u9-2.3.3-0ubuntu1~12.04.1 [37.8 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe openjdk-7-jre-lib all 7u9-2.3.3-0ubuntu1~12.04.1 [5,537 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-globalmenu i386 16.0.2+build1-0ubuntu0.12.04.1 [49.8 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox i386 16.0.2+build1-0ubuntu0.12.04.1 [20.4 MB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-gnome-support i386 16.0.2+build1-0ubuntu0.12.04.1 [9,268 B]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-en i386 16.0.2+build1-0ubuntu0.12.04.1 [480 kB]
Fetched 65.4 MB in 7min 39s (142 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `telepathy-haze' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-status-provider-pidgin' missing, assuming package has no files currently installed.
(Reading database ... 192633 files and directories currently installed.)
Preparing to replace apparmor 2.7.102-0ubuntu3.2 (using .../apparmor_2.7.102-0ubuntu3.4_i386.deb) ...
Unpacking replacement apparmor ...
Preparing to replace openjdk-7-jre 7u7-2.3.2a-0ubuntu0.12.04.1 (using .../openjdk-7-jre_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb) ...
Unpacking replacement openjdk-7-jre ...
Preparing to replace icedtea-7-jre-jamvm 7u7-2.3.2a-0ubuntu0.12.04.1 (using .../icedtea-7-jre-jamvm_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb) ...
Unpacking replacement icedtea-7-jre-jamvm ...
Preparing to replace openjdk-7-jre-headless 7u7-2.3.2a-0ubuntu0.12.04.1 (using .../openjdk-7-jre-headless_7u9-2.3.3-0ubuntu1~12.04.1_i386.deb) ...
Unpacking replacement openjdk-7-jre-headless ...
Preparing to replace openjdk-7-jre-lib 7u7-2.3.2a-0ubuntu0.12.04.1 (using .../openjdk-7-jre-lib_7u9-2.3.3-0ubuntu1~12.04.1_all.deb) ...
Unpacking replacement openjdk-7-jre-lib ...
Preparing to replace firefox-globalmenu 16.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_16.0.2+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 16.0.1+build1-0ubuntu0.12.04.1 (using .../firefox_16.0.2+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 16.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-gnome-support_16.0.2+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 16.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_16.0.2+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up apparmor (2.7.102-0ubuntu3.4) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up firefox (16.0.2+build1-0ubuntu0.12.04.1) ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (16.0.2+build1-0ubuntu0.12.04.1) ...
Setting up firefox-gnome-support (16.0.2+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (16.0.2+build1-0ubuntu0.12.04.1) ...
Setting up openjdk-7-jre-headless (7u9-2.3.3-0ubuntu1~12.04.1) ...
Installing new version of config file /etc/java-7-openjdk/security/java.security ...
Setting up openjdk-7-jre-lib (7u9-2.3.3-0ubuntu1~12.04.1) ...
Setting up openjdk-7-jre (7u9-2.3.3-0ubuntu1~12.04.1) ...
Setting up icedtea-7-jre-jamvm (7u9-2.3.3-0ubuntu1~12.04.1) ...
none@None:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
none@None:~$ 
[/HTML]

---

### Post by NikTh on 2012-10-28
Is ok now ? is it open ? 

Give these commands to see the version and packages of pidgin 

```
apt-cache policy pidgin 
dpkg -l | grep -i pidgin
```Thanks

---

### Post by CCgirl6690 on 2012-10-28
yes its open thank you ,  please see if its latest version ty
[HTML]none@None:~$ apt-cache policy pidgin 
pidgin:
  Installed: 1:2.10.3-0ubuntu1.1
  Candidate: 1:2.10.3-0ubuntu1.1
  Version table:
 *** 1:2.10.3-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     1:2.10.3-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
none@None:~$ dpkg -l | grep -i pidgin
ii  indicator-status-provider-pidgin       0.6.0-0ubuntu1                          indicator-messages status provider for pidgin
ii  nautilus-sendto                        3.0.1-2ubuntu2                          integrates Evolution and Pidgin into the Nautilus file manager
ii  pidgin                                 1:2.10.3-0ubuntu1.1                     graphical multi-protocol instant messaging client for X
ii  pidgin-data                            1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging client - data files
ii  pidgin-libnotify                       0.14-4ubuntu10                          display notification bubbles in pidgin
ii  pidgin-otr                             3.2.0-5ubuntu0.12.04.1                  Off-the-Record Messaging plugin for pidgin
ii  pidgin-plugin-pack                     2.6.3-2                                 Collection of Pidgin plugins
none@None:~$ 
[/HTML]

---

