---
title: "Minor problem with Software Update"
date: 2014-04-04
forum: General Help
---

### Post by Chris62 on 2014-04-04
Hi,

Could someone help me to solve this minor irritation, please? It is not a problem that affects the working of my machine but is just a source of irritation. I am running Ubuntu 13.10

When I run Update Manager it says that it is checking for updates and that it is downloading files from the UK server but when it has finished I get a message saying > Failed to download repository information. Check your internet connection and then offers "Retry" or "OK". Selecting "Retry" causes the whole process to start again with the same result as before, but clicking "OK" eventually results in a list of files to be installed. Although it says that it didn't download anything, it did. The list obtained after clicking "OK" shows that my internet connection is fine despite saying that it failed to download anything.

Is there a way of stopping this false information?

---

### Post by buzzingrobot on 2014-04-04
It might not be false, just not very specific.

Do an "sudo apt-get update" in a terminal and look for "404" in any messages you see about repositories that could not be contacted.  That would indicate that a repository server is offline, presumably temporarily. If it's offline, the GUI updater can't download the data it wants.

---

### Post by Chris62 on 2014-04-05
Thanks for your suggestion. I did what you said but there was no "404" in any of the messages, so I suppose I will just have to put up with it. Perhaps it will stop if I upgrade to the next release of Ubuntu. I was interested to know why it was happening for my own education and interest

---

### Post by ian-weisser on 2014-04-05
Open a terminal and use ***sudo apt-get update*** to see exactly which repository is causing the error message.

If you don't understand the (long) output, then post it here and we'll interpret it for you.

---

### Post by Chris62 on 2014-04-07
Hi ian-weisser,

Here is the output from ```
sudo apt-get update
```

> chris@chris-PC2:~$ sudo apt-get update
[[sudo] password for chris: 

Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en_GB
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en_GB
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates InRelease                       
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports InRelease                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release.gpg                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease               
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release.gpg [933 B]  
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                      
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release.gpg [933 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release [49.6 kB]             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]              
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release [49.6 kB]           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Sources                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Sources             
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [40.1 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main amd64 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en_GB
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [8,837 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Sources [81.4 kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [692 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages [108 kB]  
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]    
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Sources [68.6 kB]   
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Sources [1,348 B] 
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main amd64 Packages [225 kB] 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages [37.0 kB]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe amd64 Packages [159 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages [1,160 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [107 kB]   
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,552 B]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main i386 Packages [223 kB]  
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [37.3 kB]
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe i386 Packages [160 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [1,395 B]
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,773 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Sources [1,139 B]
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Sources [14 B]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Sources [3,538 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Sources [834 B]
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main amd64 Packages [2,135 B]
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted amd64 Packages [14 B]
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe amd64 Packages [4,690 B]
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en   
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main i386 Packages [2,140 B]
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted i386 Packages [14 B]
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe i386 Packages [4,680 B]
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse i386 Packages [709 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_GB       
Fetched 1,434 kB in 7s (186 kB/s)                                              
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
chris@chris-PC2:~$ 


When I try updating by clicking on the "Software Updater" icon it end by saying it could not download anything, and that I should d check my internet connection, but when I click on "OK" it turns out that stuff was downloaded and that my internet connection is OK

---

### Post by 23dornot23d on 2014-04-07
You have a mixed set of repos there oneiric and saucy

possible you could go into Synaptic Package manager to untick all the oneiric ones ........

or start looking in /etc/apt/sources.list

and put a 

# before the lines with oneiric in them .......... to comment them out so they do not get picked up.

looking at your output was this a series of upgrades ..... or one jump from oneiric to saucy ?

_______________________________________________________

If you cannot change things using Synaptic Package manager - settings - repository - other

Then ...........

if you post back the contents of /etc/apt/sources.list

we could have a look in it to see what may need changing .........

Which version of Ubuntu are you running ?

**lsb_release -a**

**uname -a**

---

### Post by gifford on 2014-04-07
In software sources try to uncheck install by cd-rom/dvd. It appears it is checked for 11.10...unusual.

---

### Post by 23dornot23d on 2014-04-07
Quite possible the CDROM is ticked in this view and somehow it got pointed to oneiric .........

Just incase you do not have synaptic ( sudo apt-get install synaptic ) but it should be loaded up .......

Then check it by running 

**sudo synaptic**

Then going to settings ......

[IMG]http://i.minus.com/iA7HThlJhBBbe.png[/IMG]

Probably says oneiric in there for some reason ....... but it is possibly ticked too .......

or in the next box along - in other software - there is a full listing of all the repos you are using ..... check for the ticks
in boxes alongside anything to do with oneiric and untick them ......... 

then apply / reload ......

when returning to the main screen go to the top left of of synaptic ......... press the reload button ...... see if any other errors come back

might just be a case of unticking the box - we hope .........

---

### Post by Chris62 on 2014-04-08
Thanks for your messages; first of all I had a look at sources.list and although 'oneiric' heads the list it has a '#' beside it and when I did ```
sudo synaptic
``` there was no mention of a CD in the "Ubuntu Software  window. Here is a copy of sources.list: > # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
# deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) quantal main # disabled on upgrade to quantal




Typing 'lsb_release -a' and 'uname -a' produce
> chris@chris-PC2:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
chris@chris-PC2:~$ uname -a
Linux chris-PC2 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
:

I arrived at this version of Ubuntu by doing an online upgrade. I know it is best to do a 'clean' upgrade, but at the time I did not know how to transfer my /home directory to the new version as it seemed amazingly complicated. Interestingly, there are two desktops in this house, both of them running the same version of Ubuntu and both were upgraded to the current version in the same way. One seems to have remnants of the previous version but the other does not. One, the one with the update problem, frequently says it has a system problem as soon as it has booted but carries on normally after asking if I want to report it.

---

### Post by ibjsb4 on 2014-04-08
You have one oneiric source installed.

```
deb http://archive.canonical.com/ubuntu oneiric partner

```

You need to open up your editor and comment (#) it out to read:

```
[COLOR=#ff0000]#[/COLOR]deb http://archive.canonical.com/ubuntu oneiric partner

```

First make a backup

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

```

Then open you text editor

```
gksudo gedit /etc/apt/sources.list

```

and change that line

---

### Post by 23dornot23d on 2014-04-09
Yep 7th line up from the bottom in the sources.list that was posted ..........

As lbjsb4 says - make a copy of the /etc/apt/sources.list
( always safer when messing with the sources.list to keep one )
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

Then in the original file you need a # 
at the beginning of the line with oneiric mentioned in it - so that it does not get used in future updates


Still not completely sure why its looking for a CDROM though or how it got added

Unless there is a PPA also in the directory .......
> 
**cd /etc/apt/sources.list.d**

**ls**


to see what is there also ( LS ) lower case by the way that last command - just lists what is in there.

hope something there helps ...... ( just incase a PPA is on the system doing something ..... like pointing to the CDROM )

---

### Post by ibjsb4 on 2014-04-09
```
cd /etc/apt/sources.list.d
ls

```

Don't you mean

```
ls /etc/apt/sources.list.d

```

Or a little bit better

```
ls /etc/apt/sources.list.d/*.list

```

---

### Post by Chris62 on 2014-04-10
Many thanks all you guys who have helped; the problem is now solved but it just shows how one can stare at a screen without seeing it properly

---

### Post by 23dornot23d on 2014-04-10
Good to hear - long lists like that with many commented lines are awkward - time 
to go into thread tools and mark as solved so other know ...... ty

Just in case someone should hit a similar problem ......

Checked again and the solved marker is now there ty .....

---

