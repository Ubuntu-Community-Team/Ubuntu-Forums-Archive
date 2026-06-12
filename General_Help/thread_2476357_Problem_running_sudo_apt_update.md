---
title: "Problem running sudo apt update"
date: 2022-06-23
forum: General Help
---

### Post by satimis on 2022-06-23
$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease         
Hit:3 http://security.ubuntu.com/ubuntu focal-security InRelease                      
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease                             
Hit:5 http://archive.canonical.com/ubuntu bionic InRelease                            
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease                     
Hit:7 http://hk.archive.ubuntu.com/ubuntu bionic InRelease          
Hit:8 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal InRelease
Hit:9 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:10 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:11 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:12 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

$ sudo apt list --upgradable```

Listing... Done
libgegl-0.4-0/focal 1:0.4.18+om-0ubu20.04.18~ppa amd64 [upgradable from: 0.4.22-3]
N: There is 1 additional version. Please use the '-a' switch to see it

```

$ sudo apt list -a | grep libgegl-0.4-0```


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libgegl-0.4-0/focal 1:0.4.18+om-0ubu20.04.18~ppa amd64 [upgradable from: 0.4.22-3]
libgegl-0.4-0/focal,now 0.4.22-3 amd64 [installed,upgradable to: 1:0.4.18+om-0ubu20.04.18~ppa]
libgegl-0.4-0/focal 1:0.4.18+om-0ubu20.04.18~ppa i386

```

Please advise how to fix the problem.  Thanks

Regards

---

### Post by #&amp;thj^% on 2022-06-23
Simple remove or purge the PPA >>> ppa.launchpad.net/openshot.developers
I would then report it to the maintainer of that PPA
Also check what shows here:
```
apt-cache depends 1:0.4.18+om-0ubu20.04.18~ppa
```

---

### Post by grahammechanical on 2022-06-23
You also have repositories for both Bionic and Focal. That cannot be good. What version of Ubuntu do you think you are using?

```
lsb_release -a
```

Regards

---

### Post by satimis on 2022-06-24
> **grahammechanical said:**
> You also have repositories for both Bionic and Focal. That cannot be good. What version of Ubuntu do you think you are using?

```
lsb_release -a
```

Regards
lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:        20.04
Codename:       focal

```
This PC has been running for long time.  I think more than 6~7 years.  It is a 8-core AMD CPU PC with 32G DDR3 RAM onboard.

It is time to replace it with a 16-cores AMD CPU PC and with 64G DDR5 RAM onboard.  Unfortunately I don't have time

Regards

---

### Post by satimis on 2022-06-24
> **1fallen said:**
> Simple remove or purge the PPA >>> ppa.launchpad.net/openshot.developers
Thanks for your advice.

Please advise how to remove PPA "

> 
Also check what shows here:
```
apt-cache depends 1:0.4.18+om-0ubu20.04.18~ppa
```
$ apt-cache depends 1:0.4.18+om-0ubu20.04.18~ppa```

E: No packages found

```

Regards

---

### Post by #&amp;thj^% on 2022-06-24
That baby has a lot of life left in it, Just remove the "Bionic" repos in your /etc/apt/source list.
And try again on your update and upgrade, that PPA might still be ok...we will see that after the corrections are made.

---

### Post by satimis on 2022-06-24
> **1fallen said:**
> That baby has a lot of life left in it, Just remove the "Bionic" repos in your /etc/apt/source list.
And try again on your update and upgrade, that PPA might still be ok...we will see that after the corrections are made.
$ cat /etc/apt/sources.list | grep Bionic```

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

```

Already comment out.  Whether remove the line completely?

Regards

---

### Post by deadflowr on 2022-06-24
> Already comment out. Whether remove the line completely?
I'd leave it as is.
Commented out is just as good.
But, it's your sources.list so you can do with it what you want.

---

### Post by satimis on 2022-06-24
> **deadflowr said:**
> I'd leave it as is.
Commented out is just as good.
But, it's your sources.list so you can do with it what you want.
Yes.

Usually I just comment out the line on source.list.

Then how to solve the problem on running "sudo apt update" ?

Regards

---

### Post by #&amp;thj^% on 2022-06-24
> **deadflowr said:**
> I'd leave it as is.
Commented out is just as good.
But, it's your sources.list so you can do with it what you want.

+1 Yep commented out is just as good.

---

### Post by #&amp;thj^% on 2022-06-24
> **satimis said:**
> Yes.

Usually I just comment out the line on source.list.

Then how to solve the problem on running "sudo apt update" ?

Regards
Show us again the results of :
```
sudo apt clean
sudo apt update
```

---

### Post by deadflowr on 2022-06-24
if your issue is with this command
```
apt-cache depends 1:0.4.18+om-0ubu20.04.18~ppa
```
it's because no package is listed only the version string which makes no sense to apt.

That said I do not know what the problem is.

sudo apt update's output in post #1 is fine and normal.
The apt list --upgradeable (-a) commands outputs are normal.

What problem are you having?

---

### Post by Impavidus on 2022-06-24
> **1fallen said:**
> That baby has a lot of life left in it, Just remove the "Bionic" repos in your /etc/apt/source list.
And try again on your update and upgrade, that PPA might still be ok...we will see that after the corrections are made.
Remove or replace with focal repositories, if they aren't there already. Best to have a good look at /etc/apt/sources.list first.

> **satimis said:**
> $ cat /etc/apt/sources.list | grep Bionic```

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

```

Already comment out.  Whether remove the line completely?

Regards
This is expected. grep is case sensitive and the repositories are lower case.

---

### Post by Donk^^ on 2022-06-28
> **satimis said:**
> $ cat /etc/apt/sources.list | grep Bionic```

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted

```

Already comment out.  Whether remove the line completely?

Regards

Hello
It would be better with this command:
```

grep -ri bionic /etc/apt/sources.list*

```

---

### Post by satimis on 2022-06-28
> **1fallen said:**
> Show us again the results of :
```
sudo apt clean
sudo apt update
```
$ sudo apt clean
$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease                     
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]                         
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease                                         
Hit:5 http://archive.canonical.com/ubuntu bionic InRelease                                        
Hit:6 http://hk.archive.ubuntu.com/ubuntu bionic InRelease                                        
Hit:7 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal InRelease  
Get:8 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Get:9 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:10 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:11 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:12 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Fetched 588 kB in 3s (212 kB/s)     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

Regards

---

### Post by satimis on 2022-06-28
> **deadflowr said:**
> if your issue is with this command
```
apt-cache depends 1:0.4.18+om-0ubu20.04.18~ppa
```
it's because no package is listed only the version string which makes no sense to apt.

That said I do not know what the problem is.

sudo apt update's output in post #1 is fine and normal.
The apt list --upgradeable (-a) commands outputs are normal.

What problem are you having?
On running
$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://archive.canonical.com/ubuntu bionic InRelease                                        
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]                         
Hit:4 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease                     
Hit:5 http://hk.archive.ubuntu.com/ubuntu focal InRelease                                         
Hit:6 http://hk.archive.ubuntu.com/ubuntu bionic InRelease                                        
Hit:7 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal InRelease  
Get:8 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:9 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:10 http://hk.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:11 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:12 http://hk.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Fetched 588 kB in 3s (176 kB/s)     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

But nothing to upgrade

$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Regards

---

### Post by satimis on 2022-06-28
> **Donk^^ said:**
> Hello
It would be better with this command:
```

grep -ri bionic /etc/apt/sources.list*

```
$ grep -ri bionic /etc/apt/sources.list```

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu bionic partner
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb http://download.virtualbox.org/virtualbox/debian bionic contrib
# deb-src http://download.virtualbox.org/virtualbox/debian bionic contrib
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Regards

---

### Post by ajgreeny on 2022-06-28
It seems that the only repos enabled for bionic are the source repos which I suspect the majority of users do not need so for a start comment out all the source lines which start ***deb-src*** in your sources.list file and again run ***apt update***.

If you prefer to use a GUI open ***software and updates*** which is probably in your menu system somewhere; I do not use the default Ubuntu so I'm not sure if it has the same GUI for that.

---

### Post by satimis on 2022-06-28
> **ajgreeny said:**
> It seems that the only repos enabled for bionic are the source repos which I suspect the majority of users do not need so for a start comment out all the source lines which start ***deb-src*** in your sources.list file and again run ***apt update***.

If you prefer to use a GUI open ***software and updates*** which is probably in your menu system somewhere; I do not use the default Ubuntu so I'm not sure if it has the same GUI for that.
Comment out all the lines on source.list stating "deb-src"

$ grep -ri bionic /etc/apt/sources.list```

# deb cdrom:[Ubuntu 18.04.3 LTS _Bionic Beaver_ - Release amd64 (20190805)]/ bionic main restricted
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) bionic contrib
# deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) bionic contrib
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse

```

$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu focal InRelease  
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Hit:4 http://hk.archive.ubuntu.com/ubuntu focal InRelease                      
Get:5 http://hk.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:6 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal InRelease  
Get:7 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]   
Fetched 336 kB in 2s (175 kB/s)   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Still the same

---

### Post by ActionParsnip on 2022-06-28
You are still using Bionic sources in Focal. You need to update your sources.list file to say focal instead of bionic.

---

### Post by satimis on 2022-06-28
> **ActionParsnip said:**
> You are still using Bionic sources in Focal. You need to update your sources.list file to say focal instead of bionic.
This PC has been running for several years.  According to my recollection, Ubuntu 20.04 was installed since this PC was built.  I'm running Oracle VirtualBox on this PC.  Ubuntu 20.04 is the host.

Can I just replace all bionic with focal on /etc/apt/source.list to get it upgraded?

Thanks

Regards

---

### Post by deadflowr on 2022-06-28
I see, the package is coming from the gimp PPA, but the gimp package from the PPA is older than the version from the regular Ubuntu repositories.
What gimp version is showing as installed
```
apt policy gimp
```

---

### Post by satimis on 2022-06-28
> **deadflowr said:**
> I see, the package is coming from the gimp PPA, but the gimp package from the PPA is older than the version from the regular Ubuntu repositories.
What gimp version is showing as installed
```
apt policy gimp
```
$ apt policy gimp```

gimp:
  Installed: 2.10.18-1
  Candidate: 2.10.18-1
  Version table:
 *** 2.10.18-1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

        100 /var/lib/dpkg/status
     2.10.14+om-1ubu20.04.7~ppa 500
        500 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) focal/main amd64 Packages

```

Regards

---

### Post by ActionParsnip on 2022-06-28
I suggest you uninstall gimp. Rekove the gimp PPA then reinstall gimp

---

### Post by ajgreeny on 2022-06-28
> **ActionParsnip said:**
> You are still using Bionic sources in Focal. You need to update your sources.list file to say focal instead of bionic.
No, that is not so; all the entries for bionic repos in the sources.list file are now commented out, ie, each line in the file for bionic has a # at the start meaning they are ignored by the system.

They could be totally removed or edited to remove bionic and replace with focal but are they even needed? For most users probably not.

---

### Post by satimis on 2022-06-28
> **ActionParsnip said:**
> I suggest you uninstall gimp. Rekove the gimp PPA then reinstall gimp
-> Activities -> search
found 2 gimps there

Performed following steps;

$ sudo apt remove gimp
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgmic1 libgraphicsmagick++-q16-12 libgraphicsmagick-q16-3 libheif1
  libmypaint-1.5-1 libmypaint-common
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  gimp gimp-gmic
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 23.8 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 230266 files and directories currently installed.)
Removing gimp-gmic (2.4.5-1.1) ...
Removing gimp (2.10.18-1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...

```

-> Activities -> search
still found gimp there

Ah I recall that I have another GIMP installed on;
gimp-mathmap-22-04jammy.AppImage

Please advise how to remove it?

Thanks

**[COLOR="#FF0000"]Edit[/COLOR]**
Now I have gimp-mathmap-22-04jammy.AppImage removed

-> Activities -> search
can't find GIMP

$ apt policy gimp```

gimp:
  Installed: (none)
  Candidate: 2.10.18-1
  Version table:
     2.10.18-1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
     2.10.14+om-1ubu20.04.7~ppa 500
        500 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal/main amd64 Packages

```
Pls advise how to reinstall GIMP?

Or just run;
$ sudo apt install gimp

Or run "flatpad" / "snap" ?

Regards

---

### Post by satimis on 2022-06-28
> **ajgreeny said:**
> No, that is not so; all the entries for bionic repos in the sources.list file are now commented out, ie, each line in the file for bionic has a # at the start meaning they are ignored by the system.

They could be totally removed or edited to remove bionic and replace with focal but are they even needed? For most users probably not.
Ubuntu 20.04 (host of VirtualBox) on this PC has been running for years.  I can't remember any application running here still need bionic?

Just found;
Ubutun 20.04 VM, having GIMP installed, has this problem on running "sudo apt update"

Ubuntu 20.04 VM without GIMP installed, doesn't has this problem on running  "sudo apt update"

Regards

---

