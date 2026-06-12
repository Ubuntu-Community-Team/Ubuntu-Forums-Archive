---
title: "ubuntu 14.04 trusty . broken package system"
date: 2015-05-03
forum: General Help
---

### Post by Johnathan_Bar_-_Da on 2015-05-03
Hello All.. 
Im running trusty .when I go click on Software Center I see a dialogue box inside it saying package operation failed. The system says my package system has 
broken. I have tried all the clean, -f install, autoremove , and the like, but it did not improve things much. apt-get updated, chose main server for packages,
changed to i386 architecture, and disabled the ppa repo's ,but I have not backed up the sources list. terminal says that tor-geoipdb package has unmet deps...
depends to 0.2.4 but it is not going to be installed. It suggests to try -f install with no packages , or specify a solution.
I am a beginner , if anyone can offer suggestions bear in mind please to be very specific , dont just say run this, explain where and how to run it....

I am not expecting a one - click fix on this one, somehow, can you guys steer me in a better direction ?

---

### Post by bapoumba on 2015-05-03
Could you please open a terminal and post the output to :

```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by v3.xx on 2015-05-03
If you apt-get update/upgrade, it should give you error reports.  Could you post those errors.

Also, check to be sure that ppa's are removed or disabled in your sources.list.d file.

How did you change to 32bit?  To change from 64 to 32bit, requires a reinstall of Ubuntu.

---

### Post by Johnathan_Bar_-_Da on 2015-05-03
Thanks ,Merci , I appreciate ...

Bapoumba , when I put in

```
cat -n /etc/apt/sources.list    it gives

1	# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
     2	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted #Added by software-properties
     3	
     4	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     5	# newer versions of the distribution.
     6	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
     7	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe multiverse #Added by software-properties
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
    12	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe restricted multiverse main #Added by software-properties
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team. Also, please note that software in universe WILL NOT receive any
    16	## review or updates from the Ubuntu security team.
    17	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
    18	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
    26	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
    27	
    28	## N.B. software from this repository may not have been tested as
    29	## extensively as that contained in the main release, although it includes
    30	## newer versions of some applications which may provide useful features.
    31	## Also, please note that software in backports WILL NOT receive any review
    32	## or updates from the Ubuntu security team.
    33	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
    34	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse #Added by software-properties
    35	
    36	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
    37	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe restricted multiverse main #Added by software-properties
    38	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
    39	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    46	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    47	
    48	## This software is not part of Ubuntu, but is offered by third-party
    49	## developers who want to ship their latest software.
    50	# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    51	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```


```
ls -la /etc/apt/sources.list.d




total 24
drwxr-xr-x 2 root root 4096 May  3 08:07 .
drwxr-xr-x 6 root root 4096 Jul  6  2014 ..
-rw-r--r-- 1 root root  126 May  3 08:13 fta-gnome3-trusty.list
-rw-r--r-- 1 root root  126 May  3 08:13 fta-gnome3-trusty.list.save
-rw-r--r-- 1 root root  142 May  3 08:13 upubuntu-com-tor64-trusty.list
-rw-r--r-- 1 root root  142 May  3 08:13 upubuntu-com-tor64-trusty.list.save

```

```
tail -v -n +1 /etc/apt/sources.list.d/*


==> /etc/apt/sources.list.d/fta-gnome3-trusty.list <==
# deb [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main


==> /etc/apt/sources.list.d/fta-gnome3-trusty.list.save <==
# deb [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main


==> /etc/apt/sources.list.d/upubuntu-com-tor64-trusty.list <==
# deb [http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu](http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu](http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu) trusty main


==> /etc/apt/sources.list.d/upubuntu-com-tor64-trusty.list.save <==
# deb [http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu](http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu](http://ppa.launchpad.net/upubuntu-com/tor64/ubuntu) trusty main
```


thanks for looking at it...

---

### Post by Johnathan_Bar_-_Da on 2015-05-03
v3.xx

sudo apt-get update      gives

```
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg         
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release               
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [63,5 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release [63,5 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [114 kB]       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [2 564 B]    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [4 773 B]    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [195 kB]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages [506 kB]   
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages [9 238 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages [274 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [11,8 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [495 kB]    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [9 256 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [275 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [11,9 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse amd64 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en         
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources [21,9 kB]    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources [2 061 B]  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources [1 922 B]  
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources [79,6 kB]        
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main amd64 Packages [264 kB]  
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted amd64 Packages [8 875 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe amd64 Packages [101 kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse amd64 Packages [3 451 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [253 kB]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [8 846 B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [101 kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [3 643 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_ZA                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_ZA              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_ZA              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_ZA                
Fetched 2 887 kB in 34s (83,2 kB/s)                                            
Reading package lists... Done
```

the upgrade command returns this :


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 tor-geoipdb : Depends: tor (>= 0.2.4.20-1) but it is not installed
E: Unmet dependencies. Try using -f.

```


Thank you

---

### Post by dino99 on 2015-05-03
Why are you using third party packages as they often introduce conflicts about the versions ? Do you really need fta's ppa ? and what about 'tor' which have an issue ? (purge it)
On the other side, software-center is not the most userfriendly (even if its the default's ubuntu one) and stable package-manager; better to install & use 'synaptic
> sudo apt-get install synaptic
> sudo apt-get purge tor*
> sudo apt-get autoremove

then 'extras.ubuntu.com' repo is no more active, disable it inside synaptic (top bar Settings > Repositories) and update again

---

### Post by bapoumba on 2015-05-03
You still have the tor-geoipdb package installed. your ppas being commented out, the package manager looks for dependencies that are not in the ubuntu repositories, thus the error.
It is possible that you will have to re-enable the ppa to remove the package.

What does return :
```
sudo appt-get remove tor-geoipdb
```

---

### Post by Johnathan_Bar_-_Da on 2015-05-03
hi Bapoumba,

well I removed that geo-ipdb file , then it looks like...Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
  linux-headers-3.13.0-43 linux-headers-3.13.0-43-generic
  linux-image-3.13.0-37-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-37-generic linux-image-extra-3.13.0-43-generic
  linux-signed-image-3.13.0-37-generic linux-signed-image-3.13.0-43-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  tor-geoipdb
0 upgraded, 0 newly installed, 1 to remove and 30 not upgraded.
1 not fully installed or removed.
After this operation, 2 712 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 645883 files and directories currently installed.)
Removing tor-geoipdb (0.2.4.20-1) ...


Perhaps it will be faster for me to install the distro fresh and start again. As always this

has been a learning experience.....

---

### Post by bapoumba on 2015-05-03
Well, did it remove the file with success ? The bottom part of the output is missing.

If it did, please run 
```
sudo apt-get update
sudo apt-get upgrade
```

You will run autoremove when all is clear.

As far as reinstalling, I'd not do it right now. At least please try the update/upgrade.

---

