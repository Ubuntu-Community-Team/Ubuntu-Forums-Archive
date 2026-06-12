---
title: "[ununtu] Failed to fetch http://....."
date: 2016-06-12
forum: General Help
---

### Post by backfour94 on 2016-06-12
Am trying to update the software on my computer but am getting errors 

Looking at various threads have tried :

```
 sudo apt-get update && sudo apt-get upgrade
```

to which I get:

```
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates InRelease [65.9 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse amd64 Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/multiverse amd64 Packages [6,256 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe amd64 Packages   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/universe amd64 Packages [100 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main amd64 Packages       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/main amd64 Packages [228 kB]      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted amd64 Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) wily-updates/restricted amd64 Packages [13.3 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe amd64 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/restricted amd64 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/multiverse amd64 Packages                   
Fetched 414 kB in 7s (54.2 kB/s)                                               
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/wily/InRelease](http://archive.ubuntu.com/ubuntu/dists/wily/InRelease)  Unable to find expected entry 'main/binary-i186/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/InRelease](http://security.ubuntu.com/ubuntu/dists/wily-security/InRelease)  Unable to find expected entry 'multiverse/binary-i186/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/wily-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/wily-updates/InRelease)  Unable to find expected entry 'multiverse/binary-i186/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


Have tried changing the server but I get the same thing.

Any help welcome and I think this is stopping me updating to 16.04, currently on 15.10

---

### Post by Bashing-om on 2016-06-12
backfour94; Hello ...

I have not a clue how:
> 
 'multiverse/binary-[color=red]i186[/color]/Packages'

this type file descriptor could be generated . I surely do not see it as valid !

Let's begin the process of discovery by examining the source list file(s).
Post back - between code tags - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]it be in the process
[INDENT][INDENT][INDENT]somewhere
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by backfour94 on 2016-06-12
```

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
#deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


==> /etc/apt/sources.list.d/opera-stable.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-wily.list <==
# deb http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main

==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-wily.list.distUpgrade <==
# deb http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main

==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-wily.list.save <==
# deb http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main
# deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu wily main

```

---

### Post by Bashing-om on 2016-06-12
backfour94; Well ..

Presently as is .. not a 3rd party software issue as all are disabled .

What about the /etc/apt/sources.list ?

[INDENT][INDENT]cause and effect
[INDENT][INDENT][INDENT]we be look'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by backfour94 on 2016-06-12
```

     1	# deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	
     6	## Major bug fix updates produced after the final release of the
     7	## distribution.
     8	
     9	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    10	## team. Also, please note that software in universe WILL NOT receive any
    11	## review or updates from the Ubuntu security team.
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    14	## team, and may not be under a free licence. Please satisfy yourself as to 
    15	## your rights to use the software. Also, please note that software in 
    16	## multiverse WILL NOT receive any review or updates from the Ubuntu
    17	## security team.
    18	
    19	## N.B. software from this repository may not have been tested as
    20	## extensively as that contained in the main release, although it includes
    21	## newer versions of some applications which may provide useful features.
    22	## Also, please note that software in backports WILL NOT receive any review
    23	## or updates from the Ubuntu security team.
    24	
    25	
    26	## Uncomment the following two lines to add software from Canonical's
    27	## 'partner' repository.
    28	## This software is not part of Ubuntu, but is offered by Canonical and the
    29	## respective vendors as a service to Ubuntu users.
    30	deb http://archive.ubuntu.com/ubuntu wily main universe restricted multiverse
    31	deb http://security.ubuntu.com/ubuntu/ wily-security multiverse universe main restricted
    32	deb http://archive.ubuntu.com/ubuntu wily-updates multiverse universe main restricted

```

---

### Post by Bashing-om on 2016-06-12
backfour94; Well, well ..

Pretty sparse source list, but [s]I do not see anything[/s] there to cause the error condition.
What results:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

Edit :
Maybe I see !
the line " deb http:/" wily-security multiverse universe main restrict "
I suggest to remove that trailing '/' from " /security.ubuntu.com/ubuntu/" . Maybe the field not in compliance with the proper format ?


see if we can isolate to a package config file.

[INDENT][INDENT]gots be a cause
[/INDENT][/INDENT]

---

### Post by deadflowr on 2016-06-12
Let's look at your architectures:
```
dpkg --print-architecture    
dpkg --print-foreign-architectures 
```
The first command prints your main system architecture.
The second will print any that you added.
i186 is not any architect type, never was.

I'd run this to remove it as one:
```
sudo dpkg --remove-architecture i186
```
and re-run apt-get update.

---

### Post by backfour94 on 2016-06-12
Thank you thank you thank you both very much

the 'foreign' did show i386 twice, and the remove got rid of one of them

but the process does now look to be clear.

now all I have to do is free enough space for the upgrade on /root :-)

Thanks again

---

