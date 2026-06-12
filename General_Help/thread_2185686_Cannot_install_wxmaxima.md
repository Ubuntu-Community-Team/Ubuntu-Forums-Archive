---
title: "Cannot install wxmaxima"
date: 2013-11-03
forum: General Help
---

### Post by kaurie on 2013-11-03
I am running Ubuntu 12.04 64 bit

Some months agao I installed Xmaxima and found it very useful. I now want to install wxmaxima to make my Linux machine compatable with my Windows machine. (Both versions of Maxima have benefits for me).

So using the Ubuntu Software centre I located wxmaxima and clicked install
I get the message requires>  installation of untrusted packages 
details shows>  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common ttf-jsmath wxmaxima
Clicking "OK" aborted the intallation
Clicking  "Repair"  gives me the message > Failed to download repository information and details gives a long list started by  > W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  404  Not Found

Any help appreciated

---

### Post by kaurie on 2013-11-03
Sorry I was going to post this 

```
sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                       
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release.gpg [198 B]        
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release.gpg [198 B]          
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release.gpg [198 B]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Sources                                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main i386 Packages  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_AU
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en

```

---

### Post by Bashing-om on 2013-11-03
kaurie; Hi !

So far so good, update output looks good.

Post back -preferably between code (#) tags rather than quotes to maintain the formatting - of terminal codes:
```

sudo apt-get upgrade
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```

will tell a tale.

[INDENT][INDENT]will see what we can see
[/INDENT][/INDENT]

---

### Post by kaurie on 2013-11-04
Thanks 

I am not at all sure what I am doing but here goes

> sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

>  cat -n /etc/apt/sources.list
     1	#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
     2	
     3	#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
     4	#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
     5	
     6	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     7	# newer versions of the distribution.
     8	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
     9	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    14	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
    20	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
    21	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
    22	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
    30	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
    31	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    32	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    40	deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    41	
    42	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    43	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    44	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    45	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    47	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    48	
    49	## Uncomment the following two lines to add software from Canonical's
    50	## 'partner' repository.
    51	## This software is not part of Ubuntu, but is offered by Canonical and the
    52	## respective vendors as a service to Ubuntu users.
    53	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    54	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    59	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


> ls -ls /etc/apt/sources.list.d
total 0

---

### Post by Bashing-om on 2013-11-04
kaurie; Hi !

The outputs look to be in order to me. I presently see no reason to have a problem in this instance!
However, this confuses me:
> 
details shows
libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common ttf-jsmath wxmaxima

as an "apt-cache show" reference:
> 
Version: 12.04.0-1
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libwxbase2.8-0 (>= 2.8.12.1), libwxgtk2.8-0 (>= 2.8.12.1), maxima (>= 5.18), maxima-doc (>= 5.10.0)


so, please to show the terminal output of :
```

sudo apt-get install wxmaxima

```
To put things in context.

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by kaurie on 2013-11-04
Well that worked THANKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

In the terminal after I ran "sudo apt-get install wxmaxima" if gave the followiing information and asked if I wanted to continue. I just replied y and it installed wxmaima.

And now I have just run wxmaxima. :D:D:D:D:D

Do you have any idea why it did not and then did work?  I will put solved on this but I think if your comment would be very  helpful to the people who have similar problems

```
sudo apt-get install wxmaxima
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-36 linux-headers-3.2.0-36-generic nvidia-settings
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common ttf-jsmath
The following NEW packages will be installed:
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common ttf-jsmath wxmaxima
0 upgraded, 9 newly installed, 0 to remove and 6 not upgraded.
Need to get 2,055 kB of archives.
After this operation, 8,377 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libgnomecanvas2-common all 2.30.3-1ubuntu1.1 [9,120 B]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libgnomecanvas2-0 amd64 2.30.3-1ubuntu1.1 [101 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe libgnomecups1.0-1 amd64 0.2.3-4 [60.7 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe libgnomeprint2.2-data all 2.18.8-3ubuntu1 [131 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe libgnomeprint2.2-0 amd64 2.18.8-3ubuntu1 [232 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe libgnomeprintui2.2-common all 2.18.6-3ubuntu1 [226 kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe libgnomeprintui2.2-0 amd64 2.18.6-3ubuntu1 [115 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe wxmaxima amd64 11.08.0-1 [804 kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe ttf-jsmath all 0.090709+0-1 [375 kB]       
Fetched 2,055 kB in 7s (286 kB/s)                                                                      
Selecting previously unselected package libgnomecanvas2-common.
(Reading database ... 667165 files and directories currently installed.)
Unpacking libgnomecanvas2-common (from .../libgnomecanvas2-common_2.30.3-1ubuntu1.1_all.deb) ...
Selecting previously unselected package libgnomecanvas2-0.
Unpacking libgnomecanvas2-0 (from .../libgnomecanvas2-0_2.30.3-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libgnomecups1.0-1.
Unpacking libgnomecups1.0-1 (from .../libgnomecups1.0-1_0.2.3-4_amd64.deb) ...
Selecting previously unselected package libgnomeprint2.2-data.
Unpacking libgnomeprint2.2-data (from .../libgnomeprint2.2-data_2.18.8-3ubuntu1_all.deb) ...
Selecting previously unselected package libgnomeprint2.2-0.
Unpacking libgnomeprint2.2-0 (from .../libgnomeprint2.2-0_2.18.8-3ubuntu1_amd64.deb) ...
Selecting previously unselected package libgnomeprintui2.2-common.
Unpacking libgnomeprintui2.2-common (from .../libgnomeprintui2.2-common_2.18.6-3ubuntu1_all.deb) ...
Selecting previously unselected package libgnomeprintui2.2-0.
Unpacking libgnomeprintui2.2-0 (from .../libgnomeprintui2.2-0_2.18.6-3ubuntu1_amd64.deb) ...
Selecting previously unselected package wxmaxima.
Unpacking wxmaxima (from .../wxmaxima_11.08.0-1_amd64.deb) ...
Selecting previously unselected package ttf-jsmath.
Unpacking ttf-jsmath (from .../ttf-jsmath_0.090709+0-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for fontconfig ...
Setting up libgnomecanvas2-common (2.30.3-1ubuntu1.1) ...
Setting up libgnomecanvas2-0 (2.30.3-1ubuntu1.1) ...
Setting up libgnomecups1.0-1 (0.2.3-4) ...
Setting up libgnomeprint2.2-data (2.18.8-3ubuntu1) ...
Setting up libgnomeprint2.2-0 (2.18.8-3ubuntu1) ...
Setting up libgnomeprintui2.2-common (2.18.6-3ubuntu1) ...
Setting up libgnomeprintui2.2-0 (2.18.6-3ubuntu1) ...
Setting up wxmaxima (11.08.0-1) ...
Setting up ttf-jsmath (0.090709+0-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by Bashing-om on 2013-11-04
kaurie; Well !

I can only surmise that the packages were held back most probably because the mirror site was not updated at the 1st instance of the install request. Thus did not have them in residence (???) . With out researching the dependencies and the reverse dependencies of the held back packages all I say is but speculation.

But, All is well that ends well.

[INDENT][INDENT]ain't ubuntu wonderful
[/INDENT][/INDENT]

---

### Post by kaurie on 2013-11-05
Yep Ubuntu is wonderful - when it works. Which in reality is most of the time. 

But then it is only wonderful because of people like you! I am very grateful as I would not have solved this on my own.

Thanks also for the explanation - it makes sense.

---

