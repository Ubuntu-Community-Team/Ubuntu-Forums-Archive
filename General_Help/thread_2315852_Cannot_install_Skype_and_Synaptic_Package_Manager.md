---
title: "Cannot install Skype and Synaptic Package Manager"
date: 2016-03-03
forum: General Help
---

### Post by ali2013 on 2016-03-03
I am new on Ubuntu. I have 14.04 and running 64bit. I tried to download both Skype and Synaptic but failed.

I followed this tutorial to download Skype:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I got 
[B][I]The following packages have unmet dependencies:
skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

[/I][/B]**I went to Sofware & Updates and chekced everything on Ubuntu Software and Other Softwareand selected United States as main server. 

I tried again the same commands above but still in vain.

Now for Synaptic, I cannot download it from Ubuntu Software Center as it gave me this after clicking on Install:**[B][I]

Package dependencies cannot be resolved

[/I][/B]**Help, I am going crazy**[B][I]
[/I][/B]

---

### Post by mastablasta on 2016-03-03
you should be able to install Skype using software center.

I am not sure what packages are not resolved with synaptic but you should get that information if you try to install it with command line:

sudo apt-get install synaptic

it should tell you what you need to install first before installing the program you want.

---

### Post by sandyd on 2016-03-03
Hi, can you post the output of the following:
```

sudo apt-get update
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
apt-cache show skype
apt-cache show synaptic
```

---

### Post by ali2013 on 2016-03-03
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 synaptic : Depends: libept1.4.12 but it is not installable
            Recommends: libgtk2-perl (>= 1:1.130) but it is not installable
            Recommends: rarian-compat but it is not installable
E: Unable to correct problems, you have held broken packages.
```

ali@ali-lol:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]             
Get:2 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]              
Get:4 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]             
Get:6 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [9,359 B]                    
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages [14 B]               
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Get:10 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources [10.1 kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security InRelease [65.9 kB]        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Get:12 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [6,306 B]     
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [72 B]                  
Get:14 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en [4,588 B]    
Get:15 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources [10.1 kB]           
Get:16 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages [5,634 B]    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [261 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [150 kB]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,547 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [712 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [338 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [691 kB] 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [339 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,947 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources [106 kB]      
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources [4,035 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources [33.3 kB] 
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources [2,767 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main amd64 Packages [430 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe amd64 Packages [124 kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse amd64 Packages [4,990 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages [402 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages [124 kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages [5,164 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en           
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en [2,570 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en [72.9 kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release [11.9 kB]                   
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources [14 B]                 
Fetched 4,115 kB in 15s (270 kB/s)                                             
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
```
ali@ali-lol:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```
```
ali@ali-lol:~$ ls -l /etc/apt/sources.list.d
total 4
-rw-r--r-- 1 root root 148 Feb 11  2014 steam.list
```
```
ali@ali-lol:~$ apt-cache show skype
Package: skype
Priority: extra
Section: net
Installed-Size: 61
Maintainer: Steve Langasek <steve.langasek@canonical.com>
Architecture: amd64
Version: 4.3.0.37-0ubuntu0.12.04.1
Depends: skype-bin
Filename: pool/partner/s/skype/skype_4.3.0.37-0ubuntu0.12.04.1_amd64.deb
Size: 16054
MD5sum: 61d508cabddd6d9ef7bc9967eb4bb2ed
SHA1: 590099bbcc9c486cf92b035d534fab0b062edd4e
SHA256: 590e13cf75d75cd94ddc33af179588654b5c7c0933b585e5e118e07143c96748
Description-en: client for Skype VOIP and instant messaging service
 Skype is software that enables the world's conversations.  Millions of
 individuals and businesses use Skype to make free video and voice calls,
 send instant messages and share files with other Skype users.  Every day,
 people also use Skype to make low-cost calls to landlines and mobiles.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call to landlines and mobiles at great rates.
 * Group chat with up to 200 people or conference call with up to 25 others.
 * Free to download.
Description-md5: a398bc8cee97c4027d64bae3fa223f58

Package: skype
Status: deinstall ok config-files
Priority: extra
Section: non-free/net
Installed-Size: 34642
Maintainer: Skype Technologies <info@skype.net>
Architecture: amd64
Version: 4.0.0.8-1
Replaces: skype-mid, skype-common
Depends: lib32stdc++6 (>= 4.1.1-21), lib32asound2 (>> 1.0.14), ia32-libs, libc6-i386 (>= 2.7-1), lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19)
Conflicts: skype-mid, skype-common
Conffiles:
 /etc/dbus-1/system.d/skype.conf newconffile
Description: Skype
 .
 Skype is software that enables the world's conversations.
 Millions of individuals and businesses use Skype to make free video and voice calls,
 send instant messages and share files with other Skype users.
 Everyday, people also use Skype to make low-cost calls to landlines and mobiles.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call to landlines and mobiles at great rates.
 * Group chat with up to 200 people or conference call with up to 25 others.
 * Free to download.
Description-md5: 4b9440d220d520781171ff875b490246

``````

ali@ali-lol:~$ apt-cache show synaptic
Package: synaptic
Priority: optional
Section: universe/admin
Installed-Size: 7676
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Michael Vogt <mvo@debian.org>
Architecture: amd64
Version: 0.81.1ubuntu1
Depends: libapt-inst1.5 (>= 0.8.16~exp12), libapt-pkg4.12 (>= 0.9.11), libc6 (>= 2.14), libept1.4.12, libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.14.0), libgtk-3-0 (>= 3.0.0), libpango-1.0-0 (>= 1.14.0), libstdc++6 (>= 4.6), libvte-2.90-9 (>= 1:0.27.2), libx11-6, libxapian22, hicolor-icon-theme
Recommends: gksu | kdebase-bin | policykit-1, libgtk2-perl (>= 1:1.130), rarian-compat
Suggests: dwww, menu, deborphan, apt-xapian-index, tasksel, software-properties-gtk
Conflicts: menu (<< 2.1.11)
Filename: pool/universe/s/synaptic/synaptic_0.81.1ubuntu1_amd64.deb
Size: 1361840
MD5sum: ab21aed1a78b3bd3cdc50180618817a1
SHA1: a53bc384418174d59aa0cdd8d9d4c5d375a7ba34
SHA256: cb7452320bbfe89083293689b017ee29bc026653f46506f69294225289014347
Description-en: Graphical package manager
 Synaptic is a graphical package management tool based on GTK+ and APT.
 Synaptic enables you to install, upgrade and remove software packages in
 a user friendly way.
 .
 Besides these basic functions the following features are provided:
  * Search and filter the list of available packages
  * Perform smart system upgrades
  * Fix broken package dependencies
  * Edit the list of used repositories (sources.list)
  * Download the latest changelog of a package
  * Configure packages through the debconf system
  * Browse all available documentation related to a package (dwww is required)
Description-md5: d4fb8e90c9684f1113e56123c017d85f
Homepage: [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 3y
Task: lubuntu-desktop, ubuntustudio-desktop
```

---

### Post by ali2013 on 2016-03-03
no skype there

---

### Post by Bucky Ball on 2016-03-03
Software and Updates> Other Software> enable 'Canonical Partners'. Then:

```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by sandyd on 2016-03-03
You're having a major package conflict.

Try running

```

sudo apt-get -f install
```

---

### Post by ali2013 on 2016-03-03
i did i get this
[B][I]
The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
[/I][/B]

---

### Post by ali2013 on 2016-03-03
just did... i got his

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 lib32stdc++6 libc6-i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

---

### Post by Bucky Ball on 2016-03-03
```
sudo apt-get autoremove
sudo apt-get install skype
```

You need to be more specific. 'I just did and got this' gives us no idea what you just did to make the resulting output and leaves us with few options for giving you support.

If you're going to post output, post the command you used to get it, please. Let us know what and whose suggestions you are using.

---

### Post by plucky on 2016-03-03
```
deb http://archive.canonical.com/ trusty partner
```

That line in your sources.list should look like
```
deb http://archive.canonical.com/ubuntu trusty partner
```

which may get rid of ```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...trusty/Release  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

and allow you to install skype.

You can also put a # in front of all the deb-src lines in your sources.list unless you need access to the source code.

Good Luck

---

### Post by ali2013 on 2016-03-03
Like I stated, I followed the command on Ubuntu link site...and got the result I published above. It keeps saying dependencies failed

---

### Post by X-RED_Tech on 2016-03-03
Are you again saying [COLOR=#000000]'I just did and got this' without actually saying what you did and what results? It's always better to post a copy of the terminal.[/COLOR]

---

### Post by Bashing-om on 2016-03-03
ali2013; Hello ..

What I do see is a conflict in your /etc/apt/sources.list file , as well as a duplication. 
In addition to the noted typo .. the added entries for 'extras' are not needed.
Yours:
> 
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

Should look similar to mine:
```

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#uncommented 23may2013
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu raring main
#commented out the source request as I have no need of source code in this install ##

```
Once the source list is corrected, now what results :
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ali2013 on 2016-03-03
where i can correct this?

---

### Post by ali2013 on 2016-03-03
which screen recorder i can use to record the whole screenas video? i will do everything to show you

---

### Post by ali2013 on 2016-03-03
OK, I will post screenshot..

First I went on this site: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I opened Terminal and copy and pasted the first command and got the result of screenshot 1. 


Then pasted the second command and result of screenshot 2 and 3. Then pasted the third command and ot screenst 4.

---

### Post by plucky on 2016-03-03
> **ali2013 said:**
> where i can correct this?

Open a terminal and run ```
sudo nano /etc/apt/sources.list
``` and you should be able to edit the sources.list file.

Good Luck

---

### Post by ali2013 on 2016-03-04
I removed Ubuntu and installed Mint. Skype, Steam and all other tools are working well without a single issue.. Long live Mint, Thanks for help.

---

### Post by mastablasta on 2016-03-04
the windows solution / remove reinstall... the second screenshot told you what is wrong. you either have held packages or there is an error in sources file.

---

### Post by Linuxisfast on 2016-03-04
Hundreds of Ubuntu installations done here, all I have to do is enable Canonical Partner repository and never ever an issue with Skype. Of all the distros I use Ubuntu is also the easiest to run Steam.

---

### Post by Bucky Ball on 2016-03-04
> **Linuxisfast said:**
> Hundreds of Ubuntu installations done here, all I have to do is enable Canonical Partner repository and never ever an issue with Skype.

+1. Also be advised that Mint is not officially supported here, although it does have a separate forum area in which ALL threads about Mint should be posted (or will be moved). 

For Mint support, the Mint forums is the place to go. They have a vibrant and active community and you'll have a much better chance of finding support.

Good luck.

---

