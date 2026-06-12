---
title: "Leocad broken re-install &quot;Unmet Dependencies&quot; need help fast"
date: 2019-11-16
forum: General Help
---

### Post by nocruoro on 2019-11-16
Earlier i was installing .zip files bonus folder In separate folders for luck, one in the first and the other in the library.bin folder and no results after opening program it opens, says default message cannot find any compatible parts and still only loads up the default parts. So i uninstalled it with remove and now
tried to uninstall and now trying to reinstall LeoCad because of folder problem but now i get unable to install program has unmet depencies and i can't troubleshoot properly what is broken. Cleaning it with commandshas not worked or the commands never find the broken register files. 

Need help. 

Installing it with terminal gives me this message
```

Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 leocad : Depends: libqt5concurrent5 (>= 5.6.0~rc) but it is not installable
          Depends: libqt5opengl5 (>= 5.0.2) but it is not installable
          Depends: libqt5printsupport5 (>= 5.0.2) but it is not installable
E: Unable to correct problems, you have held broken packages.



```

---

### Post by mörgæs on 2019-11-17
Please close all applications and post the output from ```
sudo apt update
``` and ```
sudo apt dist-upgrade
``` in CODE tags.

---

### Post by nocruoro on 2019-11-17
I separated them a bit (already up to date though)

What exactly do we need to find?

> 
**sudo apt update**
sudo password for kristjan: Hit:1 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]
Get:3 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB] 
Hit:4 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                            
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                        
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:8 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [7.976 B]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [42,1 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [16,4 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [111 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2.464 B]
Fetched 343 kB in 2s (187 kB/s)                        
sudo apt update
and
Code:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date


kristjan@kristjan-Aspire-F5-522:~$ sudo apt update
Hit:1 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:3 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                            
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                        
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
kristjan@kristjan-Aspire-F5-522:~$ and


Command 'and' not found, but can be installed with:


sudo apt install and

> 
kristjan@kristjan-Aspire-F5-522:~$ **sudo apt dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kristjan@kristjan-Aspire-F5-522:~$

---

### Post by mörgæs on 2019-11-17
Já sæll. Íslendingur, en gaman :-)

What does ```
sudo apt install leocad
``` yield?

---

### Post by nocruoro on 2019-11-17
bara þetta, only this
> kristjan@kristjan-Aspire-F5-522:~$ sudo apt install leocad
[sudo] password for kristjan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 leocad : Depends: libqt5concurrent5 (>= 5.6.0~rc) but it is not installable
          Depends: libqt5opengl5 (>= 5.0.2) but it is not installable
          Depends: libqt5printsupport5 (>= 5.0.2) but it is not installable
E: Unable to correct problems, you have held broken packages.
kristjan@kristjan-Aspire-F5-522:~$ 


This happened while trying to install extra parts in LeoCad og uninstallaði eftir mv move failed.
[https://askubuntu.com/questions/1188753/trying-to-move-a-file-between-folders-in-leocad](https://askubuntu.com/questions/1188753/trying-to-move-a-file-between-folders-in-leocad)

---

### Post by mörgæs on 2019-11-17
[https://ubuntuforums.org/showthread.php?t=2386369](https://ubuntuforums.org/showthread.php?t=2386369)

It's not considered good manners to open the same or closely related threads in more locations.

---

### Post by nocruoro on 2019-11-17
Hey i didn't try to break any rules**, i already checked that thread** but it didn't help. :confused:

 Thats why i made this topic, don't close yet.

---

### Post by mörgæs on 2019-11-17
> **nocruoro said:**
> I already checked that thread

We need you to post all output requested in it.

---

### Post by nocruoro on 2019-11-17
Everything i have is already here in the quotes, when i said 
> **nocruoro said:**
> Hey i didn't try to break any rules**, i already checked that thread** but it didn't help. :confused:

Thats why i made this topic, don't close yet.

**Then i meant i already posted all of them** in response to your first your posts came here.


Anything older was here with installation process
[https://ubuntuforums.org/showthread.php?t=2430951](https://ubuntuforums.org/showthread.php?t=2430951)

I hope we can be on good terms as Íslendingar. Ubuntu is like a maze/labyrinth for me. Good to have help.

---

### Post by mörgæs on 2019-11-18
The only help I can provide is the thread to which I linked. Please follow the steps described there and post the output.

---

### Post by nocruoro on 2019-11-18
heres all of it one last time but looks like i forgot the third onelooks like i forgot sources

> 
**sudo apt update**
sudo password for kristjan: Hit:1 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]
Get:3 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB] 
Hit:4 [http://archive.canonical.com]("http://archive.canonical.com/") bionic InRelease 
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease 
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease 
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release 
Get:8 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [7.976 B]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [42,1 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [16,4 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [111 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2.464 B]
Fetched 343 kB in 2s (187 kB/s) 
sudo apt update
and
Code:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
All packages are up to date


kristjan@kristjan-Aspire-F5-522:~$ sudo apt update
Hit:1 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) bionic-backports InRelease 
Hit:3 [http://archive.canonical.com]("http://archive.canonical.com/") bionic InRelease 
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease 
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease 
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release 
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done 
Building dependency tree 
Reading state information... Done
All packages are up to date.
kristjan@kristjan-Aspire-F5-522:~$ and


Command 'and' not found, but can be installed with:


sudo apt install and

> kristjan@kristjan-Aspire-F5-522:~$ sudo apt install leocad
[sudo] password for kristjan: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
leocad : Depends: libqt5concurrent5 (>= 5.6.0~rc) but it is not installable
Depends: libqt5opengl5 (>= 5.0.2) but it is not installable
Depends: libqt5printsupport5 (>= 5.0.2) but it is not installable
E: Unable to correct problems, you have held broken packages.
kristjan@kristjan-Aspire-F5-522:~$ 



> 
kristjan@kristjan-Aspire-F5-522:~$ **sudo apt dist-upgrade**
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kristjan@kristjan-Aspire-F5-522:~$



> [COLOR=#000000]cat /etc/apt/sources.list

## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner


# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) bionic partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) bionic partner
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) bionic-updates universe multiverse restricted
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) bionic-backports universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security universe multiverse restricted




[/COLOR]

---

### Post by mörgæs on 2019-11-18
*Sources* does normally not matter but something else does. Try to find out what Deadflowr is advising - not the actual steps but their purpose.
Good luck.

---

### Post by nocruoro on 2019-11-18
[CENTER][FONT=fixedsys]*My result to your latest answer "Already looked, looked, again, took a breather, went to work, looked again and nothing." *[/FONT]
[/CENTER]

Nothing different happens while browsing through **Deadflower's** suggestions.  Also completely i set automatic updates back to default. And tested purge commands to check leftover files from leocad.
Software Store still says You have unmet dependencies. When i trying using terminal to **force apt** type installation it keeps saying "you held broken pakcages" and trying to searching suggestions none of the answers there in similar threads from **Ask Ubuntu** seem to help.

So it seems my computer is purged but it is in a unmet dependencies and packages loop.
can programs like** Time Shift revert **my pc to a time before i first ever installed LeoCad and before it went haywire? *[COLOR=#ff0000]I'm sick of terminal codes for now.[/COLOR]*

---

### Post by deadflowr on 2019-11-20
Post back the full results of
```
apt policy libqt5concurrent5 libqt5opengl5 libqt5printsupport5 

```
(Use CODE tags
See [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
On how to use code tags)


Also what ppas and other 3rd party repositories have you added and/or removed?

---

### Post by nocruoro on 2019-11-22
> **deadflowr said:**
> Post back the full results of
```
apt policy libqt5concurrent5 libqt5opengl5 libqt5printsupport5 

```
(Use CODE tags
See [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
On how to use code tags)


Also what ppas and other 3rd party repositories have you added and/or removed?

Its seems empty
```
kristjan@kristjan-aspire-f5-522:~$ apt policy libqt5concurrent5 libqt5opengl5 libqt5printsupport5
libqt5concurrent5:
  Installed: (none)
  Candidate: (none)
  Version table:
libqt5opengl5:
  Installed: (none)
  Candidate: (none)
  Version table:
libqt5printsupport5:
  Installed: (none)
  Candidate: (none)
  Version table:
kristjan@kristjan-aspire-f5-522:~$
```

---

### Post by deadflowr on 2019-11-22
Okay, so I finally read past the first post, you don't have the main archives enabled.
run
```
sudo add-apt-repository main
sudo apt update
sudo apt install -f
```

---

### Post by nocruoro on 2019-11-23
> **deadflowr said:**
> Okay, so I finally read past the first post, you don't have the main archives enabled.
run
```
sudo add-apt-repository main
sudo apt update
sudo apt install -f
```


this is the result

[COLOR=#4b0082]```
kristjan@kristjan-aspire-f5-522:~$ sudo add-apt-repository main[sudo] password for kristjan: 
eSorry, try again.
[sudo] password for kristjan: 
'main' distribution component enabled for all sources.
Hit:1 http://is.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://is.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]   
Get:3 http://is.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB] 
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]    
Hit:5 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:7 http://ppa.launchpad.net/teejee2008/timeshift/ubuntu bionic InRelease    
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:9 http://archive.canonical.com bionic InRelease                            
Get:10 http://is.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1.019 kB]
Get:11 http://is.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1.007 kB]
Get:12 http://is.archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB] 
Get:13 http://is.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Get:14 http://is.archive.ubuntu.com/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Get:15 http://is.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]
Get:16 http://archive.ubuntu.com/ubuntu bionic/main Sources [829 kB]           
Get:17 http://is.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [992 kB]
Get:18 http://is.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1.026 kB]
Get:20 http://is.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [264 kB]
Get:21 http://is.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [199 kB]
Get:22 http://is.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [452 kB]
Get:23 http://is.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2.468 B]
Get:24 http://is.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [796 kB]
Get:25 http://is.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [615 kB]
Get:26 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42,2 kB]
Get:27 http://is.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [283 kB]
Get:28 http://is.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:29 http://is.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [73,8 kB]
Get:30 http://is.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [143 kB]
Get:31 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [116 kB]
Get:32 http://is.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7.972 B]
Get:33 http://is.archive.ubuntu.com/ubuntu bionic-backports/main i386 Packages [2.516 B]
Get:34 http://is.archive.ubuntu.com/ubuntu bionic-backports/main amd64 Packages [2.512 B]
Get:35 http://is.archive.ubuntu.com/ubuntu bionic-backports/main Translation-en [1.644 B]
Get:36 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2.464 B]
Get:37 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [573 kB]
Get:38 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [404 kB]
Get:39 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [190 kB]
Get:40 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38,5 kB]
Get:41 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [17,6 kB]
Get:42 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [41,5 kB]
Fetched 11,0 MB in 4s (2.679 kB/s)                      
Reading package lists... Done
kristjan@kristjan-aspire-f5-522:~$ sudo apt update
Hit:1 http://is.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://is.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:3 http://is.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Hit:4 http://ppa.launchpad.net/teejee2008/timeshift/ubuntu bionic InRelease    
Hit:5 http://archive.canonical.com bionic InRelease                            
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:7 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:9 http://security.ubuntu.com/ubuntu bionic-security InRelease       
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
44 packages can be upgraded. Run 'apt list --upgradable' to see them.
kristjan@kristjan-aspire-f5-522:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
kristjan@kristjan-aspire-f5-522:~$ 
```[/COLOR]

[COLOR=#008000]**Its' finally re-installed. That was a lot of hassle**[/COLOR]

---

