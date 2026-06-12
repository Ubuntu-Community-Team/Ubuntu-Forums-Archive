---
title: "VLC updates 12.04"
date: 2013-01-29
forum: General Help
---

### Post by Silvernail on 2013-01-29
I get an update notice and click on install.
It lists several for VLC that are not checked. It will not let me select them. Plus other updates.

All other updates install as intended.

The next time I get an update notice the same VLC updates will be listed but unchecked.

A look at the description shows a 2 version difference between installed and proposed.

Is this something I need to be concerned about? Is there something I need to clean up to make it go away?

---

### Post by searchfgold6789 on 2013-01-29
[LIST=1]
[*]Have you added a separate PPA for VLC in /etc/apt/sources.list (can you post it here?)
[*]Can we have more detail about the issue? When you try to select these updates, what happens? Or is the checkbox greyed out/will not check? What is the output of `sudo apt-get update && sudo apt-get -y upgrade`?
[/LIST]

---

### Post by Silvernail on 2013-01-30
> **searchfgold6789 said:**
> [LIST=1]
[*]Have you added a separate PPA for VLC in /etc/apt/sources.list (can you post it here?)

> # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

> 
[*]Can we have more detail about the issue? When you try to select these updates, what happens? Or is the checkbox greyed out/will not check? What is the output of `sudo apt-get update && sudo apt-get -y upgrade`?
[/LIST]
Evidently something needed upgrading. I got a 114 lines of action on the screen. Do I need to post it?

Let me run update manager before you answer.

Dave

---

### Post by Silvernail on 2013-01-30
Ok. Ran 'sudo update-manager' and the same results. The squares do not appear to be grayed out. Just won't accept a check mark.

How ever the line 'Security Updates' is checked and will uncheck.

thanks Dave

---

### Post by searchfgold6789 on 2013-01-30
> **Silvernail said:**
> Evidently something needed upgrading. I got a 114 lines of action on the screen. Do I need to post it?

Let me run update manager before you answer.

Dave
Yes, you can paste the output to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and give us the link, or when you make a reply to this thread, select it all, and click the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button to put it in code tags.

---

### Post by Silvernail on 2013-01-30
```
dave@Dafydd:~$ sudo apt-get update && sudo apt-get -y upgrade
[sudo] password for dave: 
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                                   
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                          
Ign http://deb.opera.com stable InRelease                                                                                     
Ign http://extras.ubuntu.com precise InRelease                       
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Ign http://security.ubuntu.com precise-security InRelease                                             
Hit http://us.archive.ubuntu.com precise Release                     
Hit http://deb.opera.com stable Release.gpg                          
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                                                         
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]                                             
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                                         
Hit http://extras.ubuntu.com precise Release                                                                                
Hit http://deb.opera.com stable Release                                                               
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]                                   
Hit http://extras.ubuntu.com precise/main Sources                                                             
Hit http://deb.opera.com stable/non-free i386 Packages                                               
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
Hit http://extras.ubuntu.com precise/main i386 Packages                                              
Ign http://extras.ubuntu.com precise/main TranslationIndex                                           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                   
Get:6 http://us.archive.ubuntu.com precise-updates/main Sources [218 kB]                             
Ign http://deb.opera.com stable/non-free TranslationIndex                                                    
Get:7 http://security.ubuntu.com precise-security/main Sources [62.4 kB]      
Get:8 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,118 B]                                            
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [76.4 kB]                                                         
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,737 B]                                                     
Get:11 http://us.archive.ubuntu.com precise-updates/main i386 Packages [489 kB]                                                  
Get:12 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]                                                      
Get:13 http://security.ubuntu.com precise-security/universe Sources [20.0 kB]                                                         
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B]                                                       
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [229 kB]                       
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                           
Ign http://extras.ubuntu.com precise/main Translation-en                                                       
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]                  
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [63.2 kB]                           
Get:18 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [9,483 B]                            
Get:19 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [176 kB]                             
Ign http://deb.opera.com stable/non-free Translation-en_US                                                     
Get:20 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]                         
Get:21 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                             
Get:22 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                               
Get:23 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,366 B]                                    
Get:24 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]               
Get:25 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]         
Get:26 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]         
Get:27 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]           
Get:28 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]     
Get:29 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise/main Translation-en            
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise/universe Translation-en                              
Ign http://deb.opera.com stable/non-free Translation-en                                       
Get:30 http://us.archive.ubuntu.com precise-updates/main Translation-en [233 kB]              
Get:31 http://security.ubuntu.com precise-security/main Translation-en [107 kB]        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                              
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Fetched 1,825 kB in 6s (282 kB/s)                                                                                                                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libvlc5 libvlccore5 vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
The following packages will be upgraded:
  gir1.2-telepathyglib-0.12 inkscape libtelepathy-glib0
3 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 18.9 MB of archives.
After this operation, 5,120 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libtelepathy-glib0 i386 0.18.2-0ubuntu1 [705 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-telepathyglib-0.12 i386 0.18.2-0ubuntu1 [58.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main inkscape i386 0.48.3.1-1ubuntu1.1 [18.1 MB]
Fetched 18.9 MB in 47s (402 kB/s)                                                                                                                     
(Reading database ... 425523 files and directories currently installed.)
Preparing to replace libtelepathy-glib0 0.18.0-1ubuntu1 (using .../libtelepathy-glib0_0.18.2-0ubuntu1_i386.deb) ...
Unpacking replacement libtelepathy-glib0 ...
Preparing to replace gir1.2-telepathyglib-0.12 0.18.0-1ubuntu1 (using .../gir1.2-telepathyglib-0.12_0.18.2-0ubuntu1_i386.deb) ...
Unpacking replacement gir1.2-telepathyglib-0.12 ...
Preparing to replace inkscape 0.48.3.1-1ubuntu1 (using .../inkscape_0.48.3.1-1ubuntu1.1_i386.deb) ...
Unpacking replacement inkscape ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up libtelepathy-glib0 (0.18.2-0ubuntu1) ...
Setting up gir1.2-telepathyglib-0.12 (0.18.2-0ubuntu1) ...
Setting up inkscape (0.48.3.1-1ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
dave@Dafydd:~$ 

```

---

### Post by searchfgold6789 on 2013-01-31
Interesting... Try running ```
sudo apt-get -y dist-upgrade
```After that, your VLC updates should install. Something may be happening that is preventing you from getting new packages from the mirror. You probably need to go under "Settings..." and ensure that update-manager is allowing you to install all types of package updates.

---

### Post by Silvernail on 2013-02-08
When I run this ```
sudo apt-get -y dist-upgrade
```
I get this
> The following packages have been kept back:
  libvlc5 libvlccore5 vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse


---

### Post by mc4man on 2013-02-08
You could post the results of this
```
apt-cache policy libvlc5 libvlccore5 vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse

```

And maybe also -
```
apt-cache policy libavcodec*
```

Or try - (you may wish to post above 1st.
```
sudo apt-get purge vlc-data
```
followed by 
```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by Silvernail on 2013-02-10
Either the porblem fixed itself, or one of the suggestions you guys offered did.

Thanks for your help
Dave

Problem solved

---

