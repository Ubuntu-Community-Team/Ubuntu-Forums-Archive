---
title: "Failure to download extra data files -- NOT for flash plugin"
date: 2013-11-05
forum: General Help
---

### Post by blacksh33p on 2013-11-05
Guys, not sure what else to do now, hoping somebody can give me a hand. I'm using 12.04.  At one point I installed Netflix (I think I did it through the software center) and then I uninstalled it (with software center) later that day. 

After an update a couple months later, I started getting the notification of failure to download extra data files, for redbox-desktop. So I've been googling that every couple days for a month or two, hoping for something new because I already tried all the advice from the search results including:
[https://bugs.launchpad.net/netflix-desktop/+bug/1225444](https://bugs.launchpad.net/netflix-desktop/+bug/1225444)
[http://askubuntu.com/questions/249560/netflix-desktop-no-longer-works-after-update](http://askubuntu.com/questions/249560/netflix-desktop-no-longer-works-after-update)
and maybe another one or two that I can't find again.

Anyway, I'm getting the notification every single morning and its driving me insane. Its like getting kicked in the nuts every morning for being too dumb to figure it out.. Any ideas?

---

### Post by Bashing-om on 2013-11-05
blacksh33p; Hi ! Welcome to the forum .

Let's see if we can find out what is "calling home" !

We will want to see the errors and the context of those errors from the results of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

and to see what might be doing the "calling" post back these outputs:
```

cat -n /etc/apt/sources.list 
ls -la /etc/apt/sources.list.d

```
Place these outputs between code tags:
 //
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-05
First, huge thx for the reply! Here are the outputs.

From update:
```

blacksheep@blacksheep-Latitude-D620:~$ sudo apt-get update
[sudo] password for blacksheep: 
Hit http://dl.google.com stable Release.gpg                                                                                                                                 
Hit http://dl.google.com stable Release.gpg                                                                                                                                 
Hit http://dl.google.com stable Release                                                                                                                                     
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                              
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                  
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                                                          
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                   
Hit http://dl.google.com stable Release                                                    
Hit http://ppa.launchpad.net precise Release.gpg                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                        
Hit http://ppa.launchpad.net precise Release.gpg                                                                                        
Hit http://extras.ubuntu.com precise Release.gpg                                                                                        
Hit http://us.archive.ubuntu.com precise Release                                                                                        
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                    
Hit http://dl.google.com stable/main i386 Packages                                                                                              
Ign http://dl.google.com stable/main TranslationIndex                                                                      
Hit http://ppa.launchpad.net precise Release.gpg                                                                           
Hit http://ppa.launchpad.net precise Release.gpg                                                     
Hit http://ppa.launchpad.net precise Release.gpg                                                     
Hit http://ppa.launchpad.net precise Release.gpg                                                     
Hit http://ppa.launchpad.net precise Release                                                                               
Hit http://ppa.launchpad.net precise Release                                                                               
Hit http://dl.google.com stable/main i386 Packages                                                                                                
Hit http://extras.ubuntu.com precise Release                                                                                                      
Ign http://dl.google.com stable/main TranslationIndex                                                                                             
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]                                                         
Hit http://ppa.launchpad.net precise Release                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                                        
Hit http://ppa.launchpad.net precise Release                                                                   
Hit http://ppa.launchpad.net precise Release                                                                                         
Hit http://us.archive.ubuntu.com precise-backports Release                                                                                                  
Hit http://extras.ubuntu.com precise/main Sources                                                                                                           
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
Hit http://ppa.launchpad.net precise Release                                                                               
Hit http://ppa.launchpad.net precise/main Sources                                                                          
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                 
Hit http://ppa.launchpad.net precise/main Sources                                                                          
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                    
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                           
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                        
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                              
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                          
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [424 kB]                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                               
Hit http://ppa.launchpad.net precise/main Sources                                                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                               
Hit http://ppa.launchpad.net precise/main Sources                                                                        
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                  
Get:6 http://security.ubuntu.com precise-security/main Sources [92.1 kB]                                                 
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                         
Hit http://ppa.launchpad.net precise/main Sources                                                                                  
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                             
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                             
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                          
Hit http://ppa.launchpad.net precise/main Sources                                                                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                             
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                   
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                                                                 
Get:8 http://security.ubuntu.com precise-security/universe Sources [29.2 kB]                                                                   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,804 B]                                                                          
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [353 kB]                                                                      
Ign http://dl.google.com stable/main Translation-en_US                                                                                                   
Ign http://dl.google.com stable/main Translation-en                                                                                
Ign http://dl.google.com stable/main Translation-en_US                                                       
Ign http://dl.google.com stable/main Translation-en                                                          
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                            
Ign http://ppa.launchpad.net precise/main Translation-en                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                  
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                  
Ign http://ppa.launchpad.net precise/main Translation-en                                                     
Ign http://extras.ubuntu.com precise/main Translation-en                               
Ign http://ppa.launchpad.net precise/main Translation-en_US                            
Ign http://ppa.launchpad.net precise/main Translation-en                               
Get:11 http://us.archive.ubuntu.com precise-updates/restricted Sources [7,006 B]    
Get:12 http://us.archive.ubuntu.com precise-updates/universe Sources [98.7 kB]                                                             
Get:13 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,354 B]                                                                                            
Get:14 http://us.archive.ubuntu.com precise-updates/main i386 Packages [722 kB]                                                                                             
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]                                                                                       
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [87.8 kB]                                                                                         
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                                                 
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                    
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                                                 
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                    
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,640 B]                                                                                       
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                                                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                                                 
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                                                 
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                                                   
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                                         
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                                                   
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                                                   
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                                                     
Get:18 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]                                                                                      
Get:19 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [225 kB]                                                                                         
Get:20 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.2 kB]                                                                                      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                                                                                      
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                                                
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                                                
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                                                  
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
Fetched 2,183 kB in 11s (198 kB/s)                                                                                                                                          
Reading package lists... Done

```

Upgrade I got nothing because I already did it earlier today.


Here's the output for sources.list:
```

blacksheep@blacksheep-Latitude-D620:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted
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
    57    # deb http://packages.medibuntu.org/ precise free non-free
    58    # deb-src http://packages.medibuntu.org/ precise free non-free
blacksheep@blacksheep-Latitude-D620:~$ 


```

and from sources.list.d:
```

blacksheep@blacksheep-Latitude-D620:~$ ls -la /etc/apt/sources.list.d
total 108
drwxr-xr-x 2 root root 4096 Oct 20 21:44 .
drwxr-xr-x 7 root root 4096 Oct 12 15:57 ..
-rw-r--r-- 1 root root  132 Nov  3 10:49 diesch-testing-precise.list
-rw-r--r-- 1 root root  132 Nov  3 10:49 diesch-testing-precise.list.save
-rw-r--r-- 1 root root  142 Nov  3 10:49 ehoover-compholio-precise.list
-rw-r--r-- 1 root root  142 Nov  3 10:49 ehoover-compholio-precise.list.save
-rw-r--r-- 1 root root  144 Nov  3 10:49 ferramroberto-gimp-precise.list
-rw-r--r-- 1 root root  144 Nov  3 10:49 ferramroberto-gimp-precise.list.save
-rw-r--r-- 1 root root  152 Nov  3 10:49 fossfreedom-packagefixes-precise.list
-rw-r--r-- 1 root root  152 Nov  3 10:49 fossfreedom-packagefixes-precise.list.save
-rw-r--r-- 1 root root  176 Nov  3 10:49 google-chrome.list
-rw-r--r-- 1 root root  176 Nov  3 10:49 google-chrome.list.save
-rw-r--r-- 1 root root   59 Nov  3 10:49 google.list
-rw-r--r-- 1 root root   59 Nov  3 10:49 google.list.save
-rw-r--r-- 1 root root  180 Apr 18  2013 google-talkplugin.list.save
-rw-r--r-- 1 root root  154 Nov  3 10:49 happy-neko-ps3mediaserver-precise.list
-rw-r--r-- 1 root root  154 Nov  3 10:49 happy-neko-ps3mediaserver-precise.list.save
-rw-r--r-- 1 root root  150 Nov  3 10:49 otto-kesselgulasch-gimp-precise.list
-rw-r--r-- 1 root root  150 Nov  3 10:49 otto-kesselgulasch-gimp-precise.list.save
-rw-r--r-- 1 root root  160 Nov  3 10:49 stebbins-handbrake-snapshots-precise.list
-rw-r--r-- 1 root root  160 Nov  3 10:49 stebbins-handbrake-snapshots-precise.list.save
-rw-r--r-- 1 root root  140 Nov  3 10:49 transmissionbt-ppa-precise.list
-rw-r--r-- 1 root root  140 Nov  3 10:49 transmissionbt-ppa-precise.list.save
-rw-r--r-- 1 root root  144 Nov  3 10:49 webupd8team-unstable-precise.list
-rw-r--r-- 1 root root  144 Nov  3 10:49 webupd8team-unstable-precise.list.save
-rw-r--r-- 1 root root  150 Nov  3 10:49 xubuntu-dev-xfce-4_10-precise.list
-rw-r--r-- 1 root root  150 Nov  3 10:49 xubuntu-dev-xfce-4_10-precise.list.save
blacksheep@blacksheep-Latitude-D620:~$ 


```

I should add, I did re-add the ehoover-compholio ppa a week ago or so, just hoping that it might stop the failure. It didn't do anything though..

---

### Post by Bashing-om on 2013-11-05
blacksh33p; Well !

As you do not have Wine or Netflix installed, there is no need to have the  ehoover-compholio PPA on your system, calling home for no reason.
Do terminal code:
```

sudo rm /etc/apt/sources.list.d/ehoover-compholio-precise.list
sudo rm /etc/apt/sources.list.d/ehoover-compholio-precise.list.save

```
As Well, remove all other source fetch files in this directory that you KNOW have been removed from your system.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-05
Done! Also didn't need the xfce. So now I guess we wait to see if I get kicked in the junk again in the AM :)  Thanks again, so far!  I think when I was trying to remove the ehoover ppa before, I was never specifying both the .list and the .list.save.  Probably matters huh :redface:

---

### Post by Bashing-om on 2013-11-05
blacksh33p; Hey ,

I bet the deed is done !

To the best of my poor memory, a ppa removal of an application does not remove the source "fetch" files. That is left as a decision for the administrator. As to what future action that may be taken (re-install ??).

Holler back at us and let us know how it goes !

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-06
Its still kicking me! Was on screen waiting for me this morning with a smug look on its face..

---

### Post by Bashing-om on 2013-11-06
Still :
> 
notification of failure to download extra data files, for redbox-desktop

??

Hey, still has to be a source file calling home ! .. Isolating which one .. well, 
As it happens "every morning" .. is that predictable ? like maybe you have a cron job running ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-06
Yup, same message, every morning. 
I can say I haven't **knowingly** started any jobs that would call for it overnight, but then again I'm still learning this system and have a LONG way to go.

---

### Post by Bashing-om on 2013-11-06
blacksh33p; Welp,

Near as I can find out "Redbox-desktop" is affiliated with Netflix.

Let's look on your system and see what else might remain from the removal of Netflix:
```

sudo find / -name RedBox-Desktop
sudo find / -name redBox-desktop
sudo find / -name "netflix*"

``` The find command searches your entire file system - in this instance from the root directory - and will take a bit of time for each command to complete. Exercise patience.

Let's see what is found on the system and then take action.

[INDENT][INDENT]that is what I think
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-06
Nice, great appreciation for all this so far!  Here's what I got from running those searches:
```

blacksheep@blacksheep-Latitude-D620:~$ sudo find / -name RedBox-Desktop
[sudo] password for blacksheep: 
blacksheep@blacksheep-Latitude-D620:~$ sudo find / -name redBox-desktop
blacksheep@blacksheep-Latitude-D620:~$ sudo find / -name "netflix*"
/var/lib/dpkg/info/netflix-desktop.list
/var/lib/dpkg/info/netflix-desktop.postrm
blacksheep@blacksheep-Latitude-D620:~$ 


```

---

### Post by blacksh33p on 2013-11-06
So I kept experimenting with a couple more capitalization schemes, and also came up with this:

```

blacksheep@blacksheep-Latitude-D620:~$ sudo find / -name Redbox-Desktop
blacksheep@blacksheep-Latitude-D620:~$ sudo find / -name redbox-desktop
/var/lib/update-notifier/package-data-downloads/redbox-desktop
/usr/bin/redbox-desktop
/usr/share/doc/redbox-desktop
/usr/share/package-data-downloads/redbox-desktop
blacksheep@blacksheep-Latitude-D620:~$ 


```

---

### Post by Bashing-om on 2013-11-06
blacksh33p; Well !

So much for a clean (un-)install, huh .Seeing as how there is still a control file in existence, let's take advantage of it and see what/how Netflix was installed. Check the list and make sure all of them are removed:
```

cat /var/lib/dpkg/info/netflix-desktop.list

```
You guessed it .. remove them manually from the system !
Now I am continually impressed with how smart the package manager is, recon it is outsmarting it's self and calling up "/usr/share/package-data-downloads/redbox-desktop" ?


Remove all of them, and in your AM, will see what the status is huh ??

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-06
Ok, ran that (changed "netflix" to "redbox" though), came up with this:
```

blacksheep@blacksheep-Latitude-D620:~$ cat /var/lib/dpkg/info/redbox-desktop.list
/.
/usr
/usr/share
/usr/share/package-data-downloads
/usr/share/package-data-downloads/redbox-desktop
/usr/share/wine-browser-installer
/usr/share/wine-browser-installer/redbox-desktop.install-files
/usr/share/wine-browser-installer/redbox-desktop.sha256sums
/usr/share/wine-browser-installer/redbox-desktop.menu
/usr/share/applications
/usr/share/applications/redbox-desktop.desktop
/usr/share/doc
/usr/share/doc/redbox-desktop
/usr/share/doc/redbox-desktop/copyright
/usr/share/doc/redbox-desktop/changelog.gz
/usr/bin
/usr/bin/redbox-desktop
blacksheep@blacksheep-Latitude-D620:~$ 


```

The contents of package-data-downloads are:
```

blacksheep@blacksheep-Latitude-D620:/usr/share/package-data-downloads$ ls
lovefilm-desktop  ttf-mscorefonts-installer  wine-mpg2splt-installer      wine-silverlight5.1-installer
redbox-desktop~   wine-browser-installer     wine-silverlight4-installer

```
Seems like I'd be ok to just rm -r that directory? If so, the same for the wine-browser-installer directory too?

---

### Post by Bashing-om on 2013-11-06
blacksh33p; Yepper, You got it,

That is the process, Go through each file listed from "cat /var/lib/dpkg/info/redbox-desktop.list" and "rm" or "rm -r".
And lastly remove those known files from your post #s 11 and 12 ...
I expect nothing new from the control file " /var/lib/dpkg/info/netflix-desktop.postrm" but would not hurt to look prior to removing it.

[INDENT][INDENT]lean mean and Clean !
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-06
Should be all gone, I'll update again in the AM. Thx again

---

### Post by Bashing-om on 2013-11-06
blacksh33p; Roger that.

You are quite welcome, I expect to be here tomorrow too. Let us know how it goes.

[INDENT][INDENT]Read ya then[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-07
Good news is, no more failure of extra data download. But I did have a system program error notification. Looks like it still needed something I removed. According to the crash report, it was with /usr/lib/update-notifier/package-data-downloader.  The directory is still there, but its empty. Looks like it had a lot of dependencies. 

In post 14 I had looked inside the package-data-downloader directory in /usr/share/  and it looked like it could all go away. I think I might have seen it again and thought my rm didn't work, when probably I forgot I'd switched into  /usr/lib .. Any way I can get that back, or what should I do now?  ](*,)

---

### Post by Bashing-om on 2013-11-07
blacksh33p; Hey !

nope, do not think so at this time:
> 
sysop@1304mini:~$ ls -la /usr/lib/update-notifier
ls: cannot access /usr/lib/update-notifier: No such file or directory
sysop@1304mini:~$ 

That is from version 13.04, later I will verify with 12.04. As a standard install does not have it, must be from a 3rd party software.

What results:
```

sudo apt-get update
sudo apt-get upgrade

```
To see what the package manager has to relate to us.

The only thing I see that might be a problem is "ttf-mscorefonts-installer" from the /usr/share/package-data-downloads directory. If that is required for some strange reason to be (re-)installed. not a big problem - part of the "extras" package.
Will have to check from a standard install, but this install also does not have that directory.
> 
sysop@1304mini:~$ ls -la /usr/share/package-data-downloads
ls: cannot access /usr/share/package-data-downloads: No such file or directory
sysop@1304mini:~$ 


I can be wrong, but I expect that all files listed by "cat /var/lib/dpkg/info/redbox-desktop.list" to ONLY be in relation to "redbox-desktop".

I will be back, and edit this post with what I find out in the 12.04 standard install.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-07
Ok thx. Update and Upgrade are smooth, no failures or errors.

---

### Post by Bashing-om on 2013-11-07
blacksh33p; Welp, The bad news 1st.

Directory "usr/lib/update-notifier" should contain 12 entries, amongst them is the file "package-data-downloader" in my standard 12.04 install confirms.

The good news, those files are available using the liveCD.
I suggest ya copy that entire directory over onto your install.
Do you know how to mount that install partition from the liveCD and copy those files across ?

[INDENT][INDENT]if it ain't one thing it is another
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-07
Hmm, I might be able to figure that out. I need to DL the CD again first though. Doing that now.

---

### Post by Bashing-om on 2013-11-07
blacksh33p; Atta Boy !

I find the easiest way to xfer files from the liveCD is to fire up nautilus with the elevated privileges;
```

gksudo nautilus

```
click in the left pane to mount your install partition,
navigate to the destination "usr/lib/update-notifier" on the install; open a 2nd window in nautilus and navigate to same path on the liveCD.
Drag and drop the directories and files straight from one window to the other.

This is one instance I do prefer the GUI/File Manager over the terminal. Visual aid helps too !

[INDENT][INDENT]piece of cake
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-07
Seemed easy enough, except the disk isn't layed out in any type of way where I can find anything. Has the following directories:
boot
casper
dists
install
isolinux
pics
pool
preseed
ubuntu
.disk

also, the autorun, the checksum, a readme, and wubi.exe

Checked though all the directories, can't find jack.. 

Also, my /usr/lib/update-notifier directory only has 9 files, but package-data-downloader is one of them.  If I wouldn't have to buy a new window, I'd throw this through it right now.. (Of course, its not the machine's fault, its the user..)

---

### Post by Bashing-om on 2013-11-07
blacksh33p; Hey,

I expect what you see is the .iso image of what will be live liveCD.

Check the integrity of that .iso file;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn that .iso file to CD as an image;
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Set in bios to boot the CD drive as 1st boot priority
Boot the liveCD at the purple splash screen depress the shift key -> language screen, escape key to accept the default -> boot options screen;
Choose "check disk for defects";
When check complete -> choose "try ubuntu" -> desk top -> ctl+alt+t for a terminal.

edit: The file structure of the liveCD is same same as that of the real install.

The rest as advised.

[INDENT][INDENT]no body was born knowing it all
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-07
blacksh33p;

I am done for this session. I will check for your status on my morrow,

[INDENT]take care, read ya
[/INDENT]

---

### Post by blacksh33p on 2013-11-07
Sounds good, thx for the hand today. The file copying is not working out for me yet, but I did manage to compare the directory contents between the disk and the system. Its only missing one file, something like apt-check.dist. I'll have to look again to be sure. In any case, after the restart I'm getting the failure to download extra data files error all over again.  I used to be an admin for windows networks.. This is seriously kicking my ass.

---

### Post by blacksh33p on 2013-11-08
Got the file copied, I had to enable sharing and then create a config  file for nautilus in the live environment. Everything you said worked  like a charm after that. So then since I'm getting the original error  again, I did some more searching. I found a few redbox-desktop files in  /var/lib/dpkg and removed them (thought I did that yesterday). Restarted, still getting the error. Went through all the searches you originally suggested, and they come up with nothing. Something in here is pretty sneaky.

---

### Post by blacksh33p on 2013-11-08
I may have fixed it. I kept searching for another hour after the last post. Found a wine-browser-installer folder in /var/lib and removed it. Still got the error after restart. This time I ran the "retry" on that. It caused a crash and asked if I wanted to send a report. I checked out the report details and it was caused by looking for something in /usr/share/package-data-downloads. That directory didn't exist. I checked out the same path on the live disk to see what was in it, but it was empty so I went back to the system and just created the same directory. Restarted, and so far, no more error. I won't get too excited until mornin..

---

### Post by Bashing-om on 2013-11-08
blacksh33p; Good deal !

No substitute for good troubleshooting techniques !

I have this in my notes in respect to "Wine" as Netflix is a component of Wine, would not hurt to check and make sure all of these no longer exist:
$HOME/.wine
$HOME/.winetrickscache
$HOME/.config/menus/applications-merged/wine*
$HOME/.local/share/applications/wine
$HOME/.local/share/desktop-directories/wine*
$HOME/.local/share/icons/????_*.xpm
.local/share/applications/wine/Programs/
~/.netflix-desktop
~/.wine-browser
//
wine via Synaptic:
make sure all wine* and wine-gecko* are removed.

[INDENT][INDENT]eventually, will get this cleaned up
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-08
Yup, they're all gone, and no errors this morning. Looks like we did it. Thx a ton! 
As frustrating as this was, I'm glad this system finally gave me some sort of issue to learn from. Smooth seas don't make good sailors.

---

### Post by Bashing-om on 2013-11-08
blacksh33p; Great !

LOL

I wont hold my breath, but hopefully this is now a done deal and this thread can be marked as "solved" !
What can I say but when you step out from under ubuntu's umbrella of protection (repository) and install 3rd party software, then it is on you to deal with it.  And yeah, can be a learning experience ! What a file system.

[INDENT][INDENT]it's all in knowing how
[/INDENT][/INDENT]

---

### Post by blacksh33p on 2013-11-09
I'd say we can mark it solved. Might be my imagination, but the whole thing seems to work better now than before. Touche' about the 3rd party ware! In my defense I was deleting it though haha! Lesson learned.

---

### Post by Bashing-om on 2013-11-09
blacksh33p; We will see.. Want to be sure the situation is now resolved.

Removal of added 3rd party software, now you know there is a "proper" procedure, even then there remains some vestiges - rarely will the files in one's /home directory be touched. There is everything good to say about the 3rd party stuff, it is "testing" and may eventually wind up in the supported repositories. In the repository, the package manager will deal with it quite handily.

[INDENT][INDENT]what will be will be
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-11
blacksh33p; ; Hello .

Hoz it look'n ? Can you now mark this thread as "solved" ??
Only you may do so and then only if you are satisfied with the solution.
1st post -> thread tools.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

