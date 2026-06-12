---
title: "E: The method driver /usr/lib/apt/methods/htp could not be found."
date: 2013-03-12
forum: General Help
---

### Post by duronjoshua on 2013-03-12
Hello, I'm very new to Ubuntu, I've been using it for about a month or two, and am still trying to get to know the ins and outs of everything. Well, the other day I was adding some repositories and doing some usual messing around (everything seemed to be working fine at that moment and directly after), but today I tried to run "sudo apt-get update", I was returned this error: "E: The method driver /usr/lib/apt/methods/htp could not be found."
     Also, when I went to "etc/apt" I saw that I have no "sources.list" folder. 
I'm not too sure what information to give you, as I do not really know whats important. Thanks in advance to any help I receive.

---

### Post by varunendra on 2013-03-12
duronjoshua,

It seems you didn't read the Forums Code of Conduct to which you agreed while registering here and which contains -
> Do not cross post, or post the same thing in multiple locations.
Besides, bumping threads only to raise your bean counts is not acceptable. Doing so may result in warnings/infraction.

I have jailed all your 'bump' posts and the duplicate of this thread. I suggest you read the [CoC]("http://ubuntuforums.org/misc.php?do=showrules") thoroughly and avoid any such behaviour that may cause harmful action against you from staff.

Just be reasonable, patient and polite, and your experience here would be a good one.

---

### Post by Bucky Ball on 2013-03-12
Just adding to that, a bump every 24 hours is etiquette and acceptable. You can always update us on your progress, if there are any new developments, in the meantime, of course, which will have the same result.

You may want to google 'no sources.list ubuntu' and possibly add your release number to find some clues as to how to rebuild it. 

Welcome to the forums.

---

### Post by schragge on 2013-03-12
These could be just typos, but still
> **duronjoshua said:**
> "E: The method driver /usr/lib/apt/methods/ht[COLOR=red]t[/COLOR]p could not be found."
     Also, when I went to "[COLOR=red]/[/COLOR]etc/apt" I saw that I have no "sources.list" folder.However, if they aren't then you should check your [COLOR=red]/[/COLOR]etc/apt/sources.list for syntax errors (*htp*).

---

### Post by Bucky Ball on 2013-03-12
> **schragge said:**
> ... you should check your /etc/apt/sources.list for syntax errors (*htp*).

Read again. OP has no sources.list in /etc/apt. ;)

---

### Post by schragge on 2013-03-12
The OP has no sources.list in etc/apt (without the leading slash). That was all I was saying.

Anyway, here is a sources.list generator:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by varunendra on 2013-03-12
> **duronjoshua said:**
> "E: The method driver /usr/lib/apt/methods/**[COLOR="#FF0000"]htp[/COLOR]** could not be found."

> **schragge said:**
> These could be just typos........you should check your [COLOR=red]/[/COLOR]etc/apt/sources.list for syntax errors (*htp*).
Well, I took a look in /usr/lib/apt/methods/ folder and it seems to me that indeed it is a typing error in the sources.list file. The folder contains various methods that apt can accept for software sources (cdrom, file, copy, ssh ..... and http etc.). Obviously, there is no method known as 'htp'.

@ duronjoshua,
I think it may help to take a look at -
```
ls -l /etc/apt
ls -l /etc/apt/sources.list.d
[s]cat /etc/sources.list[/s]
```
just copy-paste the above commands in a terminal to avoid typing errors.

**[COLOR="#FF0000"]Edit:[/COLOR]** I myself made a big error, the last command should be -
```
cat /etc/apt/sources.list
```

---

### Post by duronjoshua on 2013-03-12
Sorry about that, I was just a little to frustrated and eager; it won't happen again.

---

### Post by duronjoshua on 2013-03-12
I've tried a source list generator, it didn't change anything (it also seems to have been deleted for some reason), I've read through what seems like almost all other threads on the topic, and they didn't help in any ways other than showing me new problems. I don't see any typing errors. I've tried all suggestions, who know's maybe I'm doing it wrong but nothing has changed. If all else fails I'll just reinstall ubuntu (running 12.10 btw) and download my baked up files.

---

### Post by duronjoshua on 2013-03-12
(If it helps, this is what I was given following Varun's instructions) 

```
duronjoshua@duronjoshua-SVT13112FXS:~$ ls -l /etc/apt
total 80
drwxr-xr-x 2 root root  4096 Mar  9 16:56 apt.conf.d
drwxr-xr-x 2 root root  4096 Oct 16 05:59 preferences.d
-rw------- 1 root root     0 Mar  9 20:44 secring.gpg
drwxr-xr-x 2 root root  4096 Mar 12 08:54 sources.list.d
-rw-r--r-- 1 root root  3411 Mar 10 16:27 sources.list.save
-rw------- 1 root root  1200 Feb 25 17:51 trustdb.gpg
-rw-r--r-- 1 root root 26164 Mar 12 08:54 trusted.gpg
-rw-r--r-- 1 root root 25803 Mar 10 16:14 trusted.gpg~
drwxr-xr-x 2 root root  4096 Mar 12 08:54 trusted.gpg.d
```
```
duronjoshua@duronjoshua-SVT13112FXS:~$ ls -l /etc/apt/sources.list.d
total 160
-rw-r--r-- 1 root root 138 Mar 12 08:54 amith-ubuntutools-quantal.list
-rw-r--r-- 1 root root 124 Mar 12 08:54 bisigi-ppa-quantal.list
-rw-r--r-- 1 root root 124 Mar 12 08:54 bisigi-ppa-quantal.list.save
-rw-r--r-- 1 root root 132 Mar 12 08:54 diesch-testing-quantal.list
-rw-r--r-- 1 root root 132 Mar 12 08:54 diesch-testing-quantal.list.save
-rw-r--r-- 1 root root 138 Mar 12 08:54 ehoover-compholio-quantal.list
-rw-r--r-- 1 root root 138 Mar 12 08:54 ehoover-compholio-quantal.list.save
-rw-r--r-- 1 root root 134 Mar 12 08:54 falk-t-j-qtsixa-quantal.list
-rw-r--r-- 1 root root 134 Mar 12 08:54 falk-t-j-qtsixa-quantal.list.save
-rw-r--r-- 1 root root 162 Mar 12 08:54 fossfreedom-rhythmbox-plugins-quantal.list
-rw-r--r-- 1 root root 162 Mar 12 08:54 fossfreedom-rhythmbox-plugins-quantal.list.save
-rw-r--r-- 1 root root  71 Mar 12 08:54 get-deb.list
-rw-r--r-- 1 root root  71 Mar 12 08:54 get-deb.list.save
-rw-r--r-- 1 root root 176 Mar 12 08:54 google-chrome.list
-rw-r--r-- 1 root root 176 Mar 12 08:54 google-chrome.list.save
-rw-r--r-- 1 root root 170 Mar 12 08:54 hannes-janetzek-enlightenment-svn-quantal.list
-rw-r--r-- 1 root root 170 Mar 12 08:54 hannes-janetzek-enlightenment-svn-quantal.list.save
-rw-r--r-- 1 root root 158 Mar 12 08:54 jconti-recent-notifications-quantal.list
-rw-r--r-- 1 root root 158 Mar 12 08:54 jconti-recent-notifications-quantal.list.save
-rw-r--r-- 1 root root 281 Mar 10 16:27 medibuntu.list.save
-rw-r--r-- 1 root root 144 Mar 12 08:54 nilarimogard-webupd8-quantal.list
-rw-r--r-- 1 root root 144 Mar 12 08:54 nilarimogard-webupd8-quantal.list.save
-rw-r--r-- 1 root root 132 Mar 12 08:54 noobslab-icons-quantal.list
-rw-r--r-- 1 root root 132 Mar 12 08:54 noobslab-icons-quantal.list.save
-rw-r--r-- 1 root root 150 Mar 12 08:54 noobslab-initialtesting-quantal.list
-rw-r--r-- 1 root root 150 Mar 12 08:54 noobslab-initialtesting-quantal.list.save
-rw-r--r-- 1 root root 146 Mar 12 08:54 noobslab-malys-themes-quantal.list
-rw-r--r-- 1 root root 146 Mar 12 08:54 noobslab-malys-themes-quantal.list.save
-rw-r--r-- 1 root root 134 Mar 12 08:54 noobslab-themes-quantal.list
-rw-r--r-- 1 root root 134 Mar 12 08:54 noobslab-themes-quantal.list.save
-rw-r--r-- 1 root root 146 Mar 12 08:54 satyajit-happy-themes-quantal.list
-rw-r--r-- 1 root root 146 Mar 12 08:54 satyajit-happy-themes-quantal.list.save
-rw-r--r-- 1 root root 112 Mar 12 08:54 steam.list
-rw-r--r-- 1 root root 112 Mar 12 08:54 steam.list.save
-rw-r--r-- 1 root root 134 Mar 12 08:54 ubuntu-wine-ppa-quantal.list
-rw-r--r-- 1 root root 134 Mar 12 08:54 ubuntu-wine-ppa-quantal.list.save
-rw-r--r-- 1 root root 138 Mar 12 08:54 upubuntu-com-gtk3-quantal.list
-rw-r--r-- 1 root root 138 Mar 12 08:54 upubuntu-com-gtk3-quantal.list.save
-rw-r--r-- 1 root root 154 Mar 12 08:54 webupd8team-y-ppa-manager-quantal.list
-rw-r--r-- 1 root root 154 Mar 12 08:54 webupd8team-y-ppa-manager-quantal.list.save
```
```
duronjoshua@duronjoshua-SVT13112FXS:~$ cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
duronjoshua@duronjoshua-SVT13112FXS:~$
```

---

### Post by varunendra on 2013-03-12
Please also post -
```
[s]cat /etc/sources.list.save[/s]
```

**[COLOR="#FF0000"]Correction-[/COLOR]**
```
cat /etc/apt/sources.list
```

---

### Post by duronjoshua on 2013-03-12
@varunendra 
cat: /etc/sources.list.save: No such file or directory

---

### Post by varunendra on 2013-03-12
Oops!! Big mistake!

It was supposed to be -
```
cat /etc/apt/sources.list.save
```

---

### Post by duronjoshua on 2013-03-12
Alright, well here's what it gave me-

```
duronjoshua@duronjoshua-SVT13112FXS:~$ cat /etc/apt/sources.list.save
deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric non-free
deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric non-free
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
deb-src mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
duronjoshua@duronjoshua-SVT13112FXS:~$
```

---

### Post by varunendra on 2013-03-12
Okay, it looks good at first glance, only the last two lines don't look so nice -

> **duronjoshua said:**
> ```

[B]deb mirror://www.getdeb.net/playdeb-mirror/hardy/// [COLOR="#FF0000"]hardy/[/COLOR]
deb-src mirror://www.getdeb.net/playdeb-mirror/hardy/// [COLOR="#FF0000"]hardy/[/COLOR][/B]
duronjoshua@duronjoshua-SVT13112FXS:~$
```
I'm not sure about the format, but the version is definitely too outdated.

Let's first restore a copy from the backup:
```
cd /etc/apt
sudo cp sources.list.save sources.list
```

Then delete the last two lines in the new file :
```
sudo sed -i '/hardy/ d' sources.list
```
Check -
```
cat /etc/apt/sources.list
```
It should return the same output as in the previous post, minus the last two lines.

If that is correct, try an update and post back if there are still errors.

**PS:**
While posting command outputs, please use 'Code' tags (follow the 'Code Tags example' link in my signature to see how)

---

### Post by schragge on 2013-03-12
[SIZE=-1]*Post deleted as **varunendra** already beat me to it.*[/SIZE]

---

### Post by duronjoshua on 2013-03-12
Okay, it deleted the last two lines as intended, but I'm still getting back "The method driver /usr/lib/apt/methods/htp could not be found." after I try to update.

---

### Post by varunendra on 2013-03-12
> **duronjoshua said:**
> Okay, it deleted the last two lines as intended, but I'm still getting back "The method driver /usr/lib/apt/methods/htp could not be found." after I try to update.
Okay, I was anticipating that. Please post :
```
grep -iR htp /etc/apt/sources.list.d
```


PS:
@ schragge,
> Post deleted as varunendra already beat me to it.
I heard somewhere - "the only thing slower (or lazier??) than a Sloth can be another sloth..";
Welcome to the Sloth family :lol:

---

### Post by duronjoshua on 2013-03-12
THERE IT IS (wut do now?) 

duronjoshua@duronjoshua-SVT13112FXS:~$ grep -iR htp /etc/apt/sources.list.d
/etc/apt/sources.list.d/get-deb.list.save:deb htp://archive.getdeb.net/ubuntu quantal-getdeb games #GetDeb Games
/etc/apt/sources.list.d/get-deb.list:deb htp://archive.getdeb.net/ubuntu quantal-getdeb games #GetDeb Games

---

### Post by varunendra on 2013-03-12
Do-
```
sudo sed -i 's:htp:http:' /etc/apt/sources.list.d/get-deb.list
```
Retry an update, and give us a different news (hopefully a good one).

---

### Post by duronjoshua on 2013-03-12
It seems to have been fixed. 

```
duronjoshua@duronjoshua-SVT13112FXS:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal Release.gpg
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal Release
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) oneiric InRelease [5,638 B]               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease [2,840 B]                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric InRelease                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free amd64 Packages/DiffIndex   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free i386 Packages/DiffIndex    
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [548 B]               
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free amd64 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free i386 Packages              
Get:6 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [597 B]        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Get:8 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [796 B]         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Get:9 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,234 B]                
Err [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free Sources                    
  404  Not found
Get:10 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,240 B]                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/non-free Translation-en             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security InRelease                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg [933 B]        
Get:18 [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb InRelease [8,127 B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security Release.gpg [933 B]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release [49.6 kB]          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:21 [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games amd64 Packages [68.4 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Get:22 [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games i386 Packages [69.4 kB]  
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security Release [49.6 kB]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                    
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources [82.0 kB]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games Translation-en_US           
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources [80.6 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources [2,932 B]
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [585 B]                   
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages [213 kB]
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [379 B]            
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [3,048 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages [173 kB]
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [379 B]             
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,938 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages [211 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages [174 kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,109 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en [91.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en     
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Sources [34.8 kB]    
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [8,664 B]                 
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [4,410 B]          
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Sources [14 B] 
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Sources [15.4 kB]
Get:49 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [4,076 B]           
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Sources [700 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main amd64 Packages [93.1 kB]
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [4,433 B]                 
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe amd64 Packages [41.9 kB]
Get:55 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [10.6 kB]          
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse amd64 Packages [1,155 B]
Get:57 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [10.6 kB]           
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main i386 Packages [92.6 kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe i386 Packages [42.5 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse i386 Packages [1,397 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Translation-en          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Translation-en    
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Translation-en [25.7 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:63 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [4,243 B]                 
Get:64 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [3,013 B]          
Get:65 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [3,013 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:66 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [8,013 B]                 
Get:67 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [5,592 B]          
Get:68 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [5,592 B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Translation-en_US 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Fetched 1,797 kB in 40s (44.8 kB/s)
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/oneiric/non-free/source/Sources](http://download.virtualbox.org/virtualbox/debian/dists/oneiric/non-free/source/Sources)  404  Not found


W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
duronjoshua@duronjoshua-SVT13112FXS:~$
```

---

### Post by varunendra on 2013-03-12
> **duronjoshua said:**
> It seems to have been fixed.
Indeed! :)

However, you seem to be using a very mixed version of repositories -
> ```

Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) **[COLOR="#FF0000"]oneiric[/COLOR]** InRelease [5,638 B]               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) **[COLOR="#FF0000"]precise[/COLOR]** InRelease [2,840 B]                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) **quantal** InRelease                                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) **oneiric** InRelease                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease 
```
I suggest you check the guide(s) again which you followed to add these repositories and change these to your currently installed version if possible.

While a different version repository 'may' work, it has always the risk of breaking dependencies, which if happened, will cause similar headache.

As for the current errors -
> W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: **Failed to fetch [COLOR="#FF0000"]cdrom[/COLOR]**:
....
....
W: Failed to fetch [http://**download.virtualbox.org/virtualbox/debian/dists/oneiric/non-free/source/Sources**](http://**download.virtualbox.org/virtualbox/debian/dists/oneiric/non-free/source/Sources**)  **[COLOR="#FF0000"]404  Not found[/COLOR]**
...
W: Failed to fetch [http://**ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/source/Sources**](http://**ppa.launchpad.net/bisigi/ppa/ubuntu/dists/quantal/main/source/Sources**)  404  Not Found
...
[LIST=1]
[*]Open **Ubuntu Software Center > Edit > Software Sources**, goto **Other Software** tab > clear the checkboxes against CDROM.
[*]Correct or disable (clear checkboxes) the repositories related to above errors.
[/LIST]

By the way, at least virtualbox does have a repository for Quantal, as well as gpg key available for it.

---

### Post by duronjoshua on 2013-03-12
Thanks for everything. You're a beautiful person, Varun.

---

### Post by varunendra on 2013-03-12
> **duronjoshua said:**
> Thanks for everything. You're a beautiful person, Varun.
..as long as I don't start showing my photos around :lolflag:

Anyway, was a pleasure I could help. Please consider marking the thread as **[Solved]** now (follow the how to link in my signature to see how).
*[COLOR="#FF0000"]**Edit:** Oops, late again.. you alreadt did![/COLOR]*

If you have more questions related to the issue, feel free to ask. If there are but unrelated to the topic, start a new thread.

:popcorn:

---

