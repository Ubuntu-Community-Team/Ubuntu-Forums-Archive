---
title: "How do I fix these APT errors? Badsig and changed codename"
date: 2023-03-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2023-03-07
[SIZE=4]Errors:[/SIZE][INDENT]On my desktop:
[/INDENT]
[INDENT=2]```
[FONT=monospace][COLOR=#000000]$ sudo apt-get update    [/COLOR]
Hit:1 http://repo.steampowered.com/steam stable InRelease 
Hit:2 http://deb.volian.org/volian scar InRelease                                                                    
Hit:3 https://packages.microsoft.com/repos/edge stable InRelease                                                     
Hit:4 http://ppa.launchpadcontent.net/dupeguru/ppa/ubuntu jammy InRelease                                            
Hit:5 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu jammy InRelease                                          
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                            
Hit:7 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                     
Hit:8 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                    
Hit:9 http://ppa.launchpad.net/openrazer/daily/ubuntu jammy InRelease                                                
Hit:10 http://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy InRelease             
Hit:11 https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Ubuntu_22.04  InRelease 
[B]Get:12 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB] 
Err:12 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
  The following signatures were invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmast
er@ubuntu.com> [/B]
Hit:13 http://ppa.launchpad.net/xtradeb/apps/ubuntu jammy InRelease 
Fetched 107 kB in 1s (125 kB/s) 
Reading package lists... Done 
[B]W: An error occurred during the signature verification. The repository is not updated and the previous index files wi
ll be used. GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were i
nvalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  The following signatures were
 invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
W: Some index files failed to download. They have been ignored, or old ones used instead.[/B]
[/FONT]
```
[/INDENT]
[INDENT] On my server:
[/INDENT]
[INDENT=2]```
[FONT=monospace][COLOR=#000000]$ sudo apt-get update        [/COLOR]
[sudo] password for chad:  
Ign:1 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 InRelease 
Hit:3 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 Release                          
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                            
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                    
Get:2 https://dl.ubnt.com/unifi/debian stable InRelease [3038 B]     
Hit:7 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy InRelease   
Hit:8 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease         
[B]Get:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB] 
Err:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
  The following signatures were invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmast
er@ubuntu.com> [/B]
Reading package lists... Done 
[B]E: Repository 'https://dl.ubnt.com/unifi/debian stable InRelease' changed its 'Codename' value from 'unifi-7.2' to 'u
nifi-7.3' 
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for 
details. 
W: An error occurred during the signature verification. The repository is not updated and the previous index files wi
ll be used. GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were i
nvalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>[/B]
[/FONT]
```
[/INDENT]
[SIZE=4]Sources:[/SIZE][INDENT]on my desktop
[/INDENT]
[INDENT=2]```
[FONT=monospace][COLOR=#000000]
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]$ [/COLOR][/FONT][FONT=monospace][COLOR=#000000]cat /etc/apt/sources.list.d/* [/COLOR]
deb http://ppa.launchpadcontent.net/dupeguru/ppa/ubuntu/ jammy main 
# deb-src http://ppa.launchpadcontent.net/dupeguru/ppa/ubuntu/ jammy main 
# deb http://gmusicbrowser.org/deb ./ 
### THIS FILE IS AUTOMATICALLY CONFIGURED ### 
# You may comment out this entry, but any other modifications may be lost. 
deb [arch=amd64] https://packages.microsoft.com/repos/edge/ stable main 
deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu/ jammy main 
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu/ jammy main 
deb http://ppa.launchpad.net/openrazer/daily/ubuntu/ jammy main 
# deb-src http://ppa.launchpad.net/openrazer/daily/ubuntu/ jammy main 
# deb https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Ubuntu_22.04/ / 
deb https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Ubuntu_22.04/ / 
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ stable steam 
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ stable steam 

# Uncomment these lines to try the beta version of the Steam launcher 
# deb [arch=amd64,i386] https://repo.steampowered.com/steam/ beta steam 
# deb-src [arch=amd64,i386] https://repo.steampowered.com/steam/ beta steam 
deb http://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu/ jammy main 
# deb-src http://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu/ jammy main 
deb http://deb.volian.org/volian/ scar main 
deb http://ppa.launchpad.net/xtradeb/apps/ubuntu/ jammy main 
# deb-src http://ppa.launchpad.net/xtradeb/apps/ubuntu/ jammy main
[/FONT]
```
```
[FONT=monospace][COLOR=#000000]$ cat /etc/apt/sources.list [/COLOR]
# deb cdrom:[Kubuntu 22.04 LTS _Jammy Jellyfish_ - Alpha amd64 (20211126)]/ jammy main multiverse restricted universe 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 
deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu/ jammy universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy universe 
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb http://archive.canonical.com/ubuntu jammy partner 
# deb-src http://archive.canonical.com/ubuntu jammy partner 

deb http://security.ubuntu.com/ubuntu jammy-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted 
deb http://security.ubuntu.com/ubuntu jammy-security universe 
# deb-src http://security.ubuntu.com/ubuntu jammy-security universe 
deb http://security.ubuntu.com/ubuntu jammy-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse 

# This system was installed using small removable media 
# (e.g. netinst, live or single CD). The matching "deb cdrom" 
# entries were disabled at the end of the installation process. 
# For information about how to configure apt package sources, 
# see the sources.list(5) manual.
[/FONT]
```
[/INDENT]
[INDENT] on my server
[/INDENT]
[INDENT=2]```
[FONT=monospace][COLOR=#000000]$ cat /etc/apt/sources.list [/COLOR]
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 
deb http://us.archive.ubuntu.com/ubuntu jammy main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://us.archive.ubuntu.com/ubuntu jammy-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu jammy universe 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy universe 
deb http://us.archive.ubuntu.com/ubuntu jammy-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://us.archive.ubuntu.com/ubuntu jammy multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy multiverse 
deb http://us.archive.ubuntu.com/ubuntu jammy-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse 

deb http://us.archive.ubuntu.com/ubuntu jammy-security main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-security main restricted 
deb http://us.archive.ubuntu.com/ubuntu jammy-security universe 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-security universe 
deb http://us.archive.ubuntu.com/ubuntu jammy-security multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu jammy-security multiverse
[/FONT]
```
```
[FONT=monospace][COLOR=#000000]$ cat /etc/apt/sources.list.d/* [/COLOR]
# deb https://www.ui.com/downloads/unifi/debian unifi-6.5 ubiquiti 
deb https://www.ui.com/downloads/unifi/debian stable ubiquiti 
deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-3.6.gpg ] https://repo.mongodb.org/apt/ubuntu xen
ial/mongodb-org/3.6 multiverse 
deb https://ppa.launchpadcontent.net/ondrej/php/ubuntu/ jammy main 
# deb-src https://ppa.launchpadcontent.net/ondrej/php/ubuntu/ jammy main
[/FONT]
```
[/INDENT]
[SIZE=4]Proxy Setting:[/SIZE][INDENT]on my desktop
[/INDENT]
[INDENT=2]```
[FONT=monospace][COLOR=#000000]$ cat /etc/apt/apt.conf.d/02proxy  [/COLOR]
Acquire::http::proxy "http://10.0.0.69:3142";[/FONT]
```[/INDENT]
[INDENT] [FONT=monospace]on my server
[/FONT][/INDENT]
[INDENT=2]```
[FONT=monospace][COLOR=#000000]$ cat /etc/apt/apt.conf.d/02proxy [/COLOR]
Acquire::http::proxy "http://127.0.0.1:3142";
[/FONT]
```
[/INDENT]

I am using apt-cacher-ng on my server, i have http**s** set to passthough, maybe there is a way to use http to the server and https to the internet? this is why i am using http in my sources files

---

### Post by TheFu on 2023-03-07
Have you already waited a day for the maintainer to fix the issue on their own?
I use apt-cacher-ng too. The settings on all my systems for it are the same, but I use a DNS name.
```
Acquire::http { Proxy "http://istar:3142"; };
```
I also passthru HTTPS ... but to a list of "approved" repos only, not everything. If a new PPA gets added, and it is approved, then I have to go change the proxy-allow settings.  We don't have many developers wanting to do too much that way, so forcing them to have local copies of any code they got off the internet is a good thing ... sometimes. ;|

---

### Post by pqwoerituytrueiwoq on 2023-03-07
been putting this off for weeks... really should deal with it

i have had held packages for a while cause of this
desktop:[INDENT]```
$ apt-cache policy grub-efi-amd64-bin grub-efi-amd64-signed shim-signed
grub-efi-amd64-bin: 
  Installed: 2.06-2ubuntu10 
  Candidate: 2.06-2ubuntu14.1 
  Version table: 
     2.06-2ubuntu14.1 500 (phased 0%) 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
 *** 2.06-2ubuntu10 500 
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     2.06-2ubuntu7 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
grub-efi-amd64-signed: 
  Installed: 1.182~22.04.1+2.06-2ubuntu10 
  Candidate: 1.187.3~22.04.1+2.06-2ubuntu14.1 
  Version table: 
     1.187.3~22.04.1+2.06-2ubuntu14.1 500 (phased 0%) 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
 *** 1.182~22.04.1+2.06-2ubuntu10 500 
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     1.180+2.06-2ubuntu7 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
shim-signed: 
  Installed: 1.51+15.4-0ubuntu9 
  Candidate: 1.51.3+15.7-0ubuntu1 
  Version table: 
     1.51.3+15.7-0ubuntu1 500 (phased 75%) 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
 *** 1.51+15.4-0ubuntu9 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
        100 /var/lib/dpkg/status
```
[/INDENT]
 server:
[INDENT]```
$ apt-cache policy python3-software-properties software-properties-common systemd-hwe-hwdb
python3-software-properties: 
  Installed: 0.99.22.3 
  Candidate: 0.99.22.6 
  Version table: 
     0.99.22.6 500 (phased 90%) 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
 *** 0.99.22.3 100 
        100 /var/lib/dpkg/status 
     0.99.22 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
software-properties-common: 
  Installed: 0.99.22.3 
  Candidate: 0.99.22.6 
  Version table: 
     0.99.22.6 500 (phased 90%) 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
 *** 0.99.22.3 100 
        100 /var/lib/dpkg/status 
     0.99.22 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
systemd-hwe-hwdb: 
  Installed: 249.11.2 
  Candidate: 249.11.3 
  Version table: 
     249.11.3 500 (phased 40%) 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
 *** 249.11.2 100 
        100 /var/lib/dpkg/status
```
[/INDENT]

---

### Post by TheFu on 2023-03-07
Did you try installing the exact version of the packages being held back?

BTW, did you see this error message and fix it?
```
E: Repository 'https://dl.ubnt.com/unifi/debian stable InRelease' changed its 'Codename' value from 'unifi-7.2' to 'unifi-7.3' 
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
```

---

### Post by pqwoerituytrueiwoq on 2023-03-07
I have not fix that one my sources call for stable not a specific version, so idk what do do about it 
[FONT=monospace]```
deb https://www.ui.com/downloads/unifi/debian stable ubiquiti
```[/FONT]

---

### Post by pqwoerituytrueiwoq on 2023-03-09
found the fix for the code name issue
```
sudo apt-get update --allow-releaseinfo-change
```
i suspect the bad sig is cause i changed https to http so i could cache it, but what is the fix aside from reverting

---

### Post by oldos2er on 2023-03-11
Have you tried [this advice]("https://itsfoss.com/solve-badsig-error-quick-tip/")?

---

### Post by pqwoerituytrueiwoq on 2023-03-11
yes

---

### Post by #&amp;thj^% on 2023-03-11
> **pqwoerituytrueiwoq said:**
>  i changed https to http so i could cache it, but what is the fix aside from reverting

My first guess is it's not fixed, please try for:
```
Repository 'https://dl.ubnt.com/unifi/debian stable InRelease' changed its 'Codename' value from 'unifi-7.2' to 'unifi-7.3' 
N: This must be accepted explicitly before updates for this repository can be applied
```
With this: 
```
sudo apt update && sudo apt install ca-certificates apt-transport-https
```
then:>(even if you have already)
```
echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
```
now:
```
sudo wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ui.com/unifi/unifi-repo.gpg 
```

Note: On some Distributions, it's possible an incompatible Java release can be installed during this step. We recommend running the following command before proceeding with this step, to restrict Ubuntu from automatically installing Java 11. If you wish to undo this later, replace "hold" with "unhold".

```
sudo apt-mark hold openjdk-11-*

```
Mine:
```
 sudo apt-mark hold openjdk-11-*
openjdk-11-jdk set on hold.
openjdk-11-doc set on hold.
openjdk-11-jdk-headless set on hold.
openjdk-11-jre set on hold.
openjdk-11-jre-headless set on hold.
openjdk-11-dbg set on hold.
openjdk-11-demo set on hold.
openjdk-11-source set on hold.
openjdk-11-jre-dcevm set on hold.
openjdk-11-jre-zero set on hold.

```
Install and upgrade the UniFi Network application with the following command:

```
sudo apt-get update && sudo apt-get install unifi -y
```
Post any errors, I usually just run a script for unifi.

---

### Post by pqwoerituytrueiwoq on 2023-03-11
had that one fixed in post #6 and [FONT=monospace][COLOR=#000000]ca-certificates apt-transport-https[/COLOR][/FONT] were already installed

though do not have it set to hold the openjdk package

this is the remaining issue:
```
[FONT=monospace][B]W: An error occurred during the signature verification. The repository is not updated and the previous index files wi
ll be used. GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were i
nvalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>[/B][/FONT]
```

---

### Post by dragonfly41 on 2023-03-12
Y PPA Manager (a GUI tool) might help. Look at Advanced features.

---

### Post by #&amp;thj^% on 2023-03-12
> **pqwoerituytrueiwoq said:**
> had that one fixed in post #6 and [FONT=monospace][COLOR=#000000]ca-certificates apt-transport-https[/COLOR][/FONT] were already installed

though do not have it set to hold the openjdk package

this is the remaining issue:
```
[FONT=monospace][B]W: An error occurred during the signature verification. The repository is not updated and the previous index files wi
ll be used. GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were i
nvalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>[/B][/FONT]
```

On 22.04 I'll break the important bits one line at a time:
```
apt-get update; apt-get install ca-certificates wget -y
```
I used wget so the above command is important.
```
wget https://get.glennr.nl/unifi/install/unifi-6.5.55.sh
```
For a clean installer: (sudo needed here)
```
bash unifi-6.5.55.sh
```
That will show install options as well. And I found that version a very stable release.
If on the off chance you need a newer version, I'll try to help with that.
Proof:
```
>> sudo apt update
Hit:1 https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease
Hit:2 http://eddie.website/repository/apt stable InRelease                                                   
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                    
Get:5 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease [7,538 B]                             
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                    
Ign:7 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 InRelease                                   
Hit:8 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                            
Hit:9 https://ppa.launchpadcontent.net/jonaski/strawberry/ubuntu jammy InRelease                             
Hit:3**_ https://dl.ubnt.com/unifi/debian unifi-6.5 InRelease         _**                                          
Get:10 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease [7,459 B]                             
Hit:11 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease                                         
Hit:12**_ https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 Release       _**                             
Get:13 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,453 B]                          
Hit:14 https://repos.codelite.org/wx3.2.0/ubuntu jammy InRelease                                             
Get:15 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,452 B]                     
Hit:17 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease                 
Hit:18 https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu jammy InRelease
Fetched 140 kB in 3s (43.6 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```
Might as well add it here for the newest version
```
wget https://get.glennr.nl/unifi/install/unifi-7.3.83.sh

```
sudo here:
```
bash unifi-7.3.83.sh
```
Upgrades as well:
```
# UniFi is already installed on your system!
# You can use my Easy Update Script to update your UniFi Network Application.


# Would you like to download and run my Easy Update Script? (Y/n) 


```
```
#########################################################################

# The latest patches have been successfully installed on your system! 


# Author   |  Glenn R.
# Email    |  glennrietveld8@hotmail.nl
# Website  |  https://GlennR.nl


```

---

### Post by pqwoerituytrueiwoq on 2023-03-12
again I got the unifi issue fixed in post #6
> **pqwoerituytrueiwoq said:**
> found the fix for the code name issue
```
sudo apt-get update --allow-releaseinfo-change
```

```

[FONT=monospace][COLOR=#54ff54]**chad@niceserver**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ apt-cache policy ca-certificates wget apt-transport-https unifi [/COLOR]
ca-certificates: 
  Installed: 20211016ubuntu0.22.04.1 
  Candidate: 20211016ubuntu0.22.04.1 
  Version table: 
 *** 20211016ubuntu0.22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
        500 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     20211016 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
wget: 
  Installed: 1.21.2-2ubuntu1 
  Candidate: 1.21.2-2ubuntu1 
  Version table: 
 *** 1.21.2-2ubuntu1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
        100 /var/lib/dpkg/status 
apt-transport-https: 
  Installed: 2.4.8 
  Candidate: 2.4.8 
  Version table: 
 *** 2.4.8 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages 
        100 /var/lib/dpkg/status 
     2.4.5 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages 
unifi: 
  Installed: 7.3.83-19645-1 
  Candidate: 7.3.83-19645-1 
  Version table: 
 *** 7.3.83-19645-1 500 
        500 https://www.ui.com/downloads/unifi/debian stable/ubiquiti amd64 Packages 
        100 /var/lib/dpkg/status[/FONT]

```
```

[FONT=monospace][COLOR=#54ff54]**chad@niceserver**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/apt/sources.list.d/100-ubnt-unifi.list  [/COLOR]
**#** deb https://www.ui.com/downloads/unifi/debian unifi-6.5 ubiquiti 
deb https://www.ui.com/downloads/unifi/debian **stable** ubiquiti[/FONT]

```
[HR][/HR]the issue i still have is with a bagsig for jammy-backports, one of the stock repos
```
[FONT=monospace][COLOR=#54ff54]**chad@niceserver**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt-get update [/COLOR]
Ign:1 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 InRelease 
Hit:2 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 Release                          
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                         
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                    
Hit:3 https://dl.ubnt.com/unifi/debian stable InRelease                                                              
Hit:7 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy InRelease 
Hit:8 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease 
Get:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB] 
Err:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
  The following signatures were invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmast
er@ubuntu.com> 
Reading package lists... Done 
W: GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were invalid: B
ADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
E: The repository 'http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease' is not signed. 
N: Updating from such a repository can't be done securely, and is therefore disabled by default. 
N: See apt-secure(8) manpage for repository creation and user configuration details.
[/FONT]
```

---

### Post by #&amp;thj^% on 2023-03-12
> **pqwoerituytrueiwoq said:**
> again I got the unifi issue fixed in post #6

That was clear then and now. ;)
```

> **pqwoerituytrueiwoq said:**
> [QUOTE=pqwoerituytrueiwoq;14134509]$ apt-cache policy ca-certificates wget apt-transport-https unifi [/COLOR]
ca-certificates: 
  Installed: 20211016ubuntu0.22.04.1 
  Candidate: 20211016ubuntu0.22.04.1 
  Version table: 
 *** 20211016ubuntu0.22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
        500 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     20211016 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
wget: 
  Installed: 1.21.2-2ubuntu1 
  Candidate: 1.21.2-2ubuntu1 
  Version table: 
 *** 1.21.2-2ubuntu1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
        100 /var/lib/dpkg/status 
apt-transport-https: 
  Installed: 2.4.8 
  Candidate: 2.4.8 
  Version table: 
 *** 2.4.8 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages 
        100 /var/lib/dpkg/status 
     2.4.5 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages 
unifi: 
  Installed: 7.3.83-19645-1 
  Candidate: 7.3.83-19645-1 
  Version table: 
 *** 7.3.83-19645-1 500 
        500 https://www.ui.com/downloads/unifi/debian stable/ubiquiti amd64 Packages 
        100 /var/lib/dpkg/status[/FONT]

```
```

[FONT=monospace][COLOR=#54ff54]**chad@niceserver**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/apt/sources.list.d/100-ubnt-unifi.list  [/COLOR]
**#** deb https://www.ui.com/downloads/unifi/debian unifi-6.5 ubiquiti 
deb https://www.ui.com/downloads/unifi/debian **stable** ubiquiti[/FONT]

```
Notice the difference with mine:
```
apt-cache policy ca-certificates wget apt-transport-https unifi 
ca-certificates:
  Installed: 20211016ubuntu0.22.04.1
  Candidate: 20211016ubuntu0.22.04.1
  Version table:
 *** 20211016ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
        100 /var/lib/dpkg/status
     20211016 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/main i386 Packages
wget:
  Installed: 1.21.2-2ubuntu1
  Candidate: 1.21.2-2ubuntu1
  Version table:
 *** 1.21.2-2ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
apt-transport-https:
  Installed: 2.4.8
  Candidate: 2.4.8
  Version table:
 *** 2.4.8 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     2.4.5 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
unifi:
  Installed: 6.5.55-16678-1
  Candidate: 6.5.55-16678-1
  Version table:
 *** 6.5.55-16678-1 500
        500 https://www.ui.com/downloads/unifi/debian unifi-6.5/ubiquiti amd64 Packages
        500 https://www.ui.com/downloads/unifi/debian unifi-6.5/ubiquiti i386 Packages
        100 /var/lib/dpkg/status


```
[QUOTE=pqwoerituytrueiwoq;14134509]
[HR][/HR]the issue i still have is with a bagsig for jammy-backports, one of the stock repos
```
[FONT=monospace][COLOR=#54ff54]**chad@niceserver**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt-get update [/COLOR]
Ign:1 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 InRelease 
Hit:2 https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 Release                          
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                         
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                    
Hit:3 https://dl.ubnt.com/unifi/debian stable InRelease                                                              
Hit:7 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy InRelease 
Hit:8 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease 
Get:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB] 
Err:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
  The following signatures were invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmast
er@ubuntu.com> 
Reading package lists... Done 
W: GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were invalid: B
ADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
E: The repository 'http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease' is not signed. 
N: Updating from such a repository can't be done securely, and is therefore disabled by default. 
N: See apt-secure(8) manpage for repository creation and user configuration details.
[/FONT]
```

That script will help but, you do have to decide

---

### Post by pqwoerituytrueiwoq on 2023-03-12
so how would a unify install script help with a bad sig when unify is not even in the related repo?

it seems like temporally disabling my cache proxy while i ran apt-get update made the issue go away

---

### Post by jared-thomas on 2023-03-13
I ran into a similar issue: I have a standalone apt-cacher-ng server and a number of Ubuntu systems all pointing to it. They were all getting the BADSIG error on archive.ubuntu.org but would update fine when set to bypass apt-cacher-ng and go directly out to the repositories. In my case, the issue was resolved by installing the apt-transport-https package on the ACNG server, then running *Start Scan and/or Expiration *with the *Force the download of index files (even having fresh ones) *enabled.

---

### Post by #&amp;thj^% on 2023-03-17
Ok i ran into this on lunar yesterday, same message as yours but "lunar" not 
"jammy"
One more attempt to help:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 871920D1991BC93C
```
just a heads up that may throw that key in a legacy mode, like it did mine.

---

### Post by pqwoerituytrueiwoq on 2023-06-05
@1fallen
did not help

@jared-thomas
no luck :(
i managed to get to to go away temporally by bypassing the apt cache server...

i did get some warning while doing this

```
Parsing metadata in uburep/dists/jammy-updates/InRelease
WARNING: File not accessible, will remove metadata of uburep/dists/jammy-updates/multiverse/dep11/Components-amd64.yml
WARNING: File not accessible, will remove metadata of uburep/dists/jammy-updates/universe/dep11/Components-amd64.yml
WARNING: File not accessible, will remove metadata of uburep/dists/jammy-updates/universe/i18n/Translation-en
Parsing metadata in uburep/dists/jammy-updates/main/binary-amd64/Packages.xz
```
```
Parsing metadata in uburep/dists/jammy-backports/InRelease
WARNING: File not accessible, will remove metadata of uburep/dists/jammy-backports/main/dep11/Components-amd64.yml
Parsing metadata in uburep/dists/jammy-backports/main/binary-amd64/Packages.xz
```

---

### Post by #&amp;thj^% on 2023-06-05
> **pqwoerituytrueiwoq said:**
> @1fallen
did not help


Neither dose this "did not help" you have been around long enough to know better. ;)
Final suggestion after talking with some of the Devs:
```
apt-key adv --refresh-keys --keyserver keyserver.ubuntu.com
```
just an example without using sudo:
```
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
Executing: /tmp/apt-key-gpghome.2G1nMLa0qS/gpg.1.sh --refresh-keys --keyserver keyserver.ubuntu.com
gpg: refreshing 11 keys from hkp://keyserver.ubuntu.com
gpg: key 32B18A1260D8DA0B: "Launchpad PPA for YannUbuntu" not changed
gpg: key 871920D1991BC93C: "Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>" not changed
gpg: key D94AA3F0EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: key 4C1CBE14852541CB: "Launchpad PPA for Panda Jim" not changed
gpg: key 22AAEA0A86A02625: "Jerry Bezencon (Linux Lite) <valtam@linuxliteos.com>" not changed
gpg: key 6B219E535C964CA1: "NordVPN <admin@nordvpn.com>" not changed
gpg: key 9BDB3D89CE49EC21: "Launchpad PPA for Mozilla Team" not changed
gpg: key FCAE110B1118213C: "Launchpad PPA for Graphics Drivers Team" not changed
gpg: key 7721F63BD38B4796: "Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>" 1 new signature
gpg: key ADAE6AD28A8F901A: "Sublime HQ Pty Ltd <support@sublimetext.com>" not changed
gpg: key F42ED6FBAB17C654: "Open Robotics <info@osrfoundation.org>" 1 new signature
gpg: Total number processed: 11
gpg:              unchanged: 9
gpg:         new signatures: 2
gpg: error writing keyring '/etc/apt/trusted.gpg': Permission denied
gpg: error reading '[stdin]': Permission denied
gpg: import from '[stdin]' failed: Permission denied
gpg: Total number processed: 0

```
Anyway good luck, and may the good force be with you...

---

### Post by pqwoerituytrueiwoq on 2023-06-05
well what else could i say, it is not like i got a error...
```

[FONT=monospace][COLOR=#54ff54]**chad@X470-Gaming-Plus**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt-key adv --refresh-keys --keyserver keyserver.ubuntu.com [/COLOR]
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)). 
Executing: /tmp/apt-key-gpghome.S0eDWlVOsz/gpg.1.sh --refresh-keys --keyserver keyserver.ubuntu.com 
gpg: refreshing 15 keys from hkp://keyserver.ubuntu.com 
gpg: key 82BB6851C64F6880: "Launchpad PPA for xtradeb Ubuntu team" not changed 
gpg: key A87015F3DA22D980: "Volian Scar Release Key (1/scar) <volian-devel@volian.org>" not changed 
gpg: key 06E85760C0A52C50: "UniFi Developers <unifi-dev@ubnt.com>" not changed 
gpg: key 871920D1991BC93C: "Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com>" not changed 
gpg: key D94AA3F0EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed 
gpg: key B90E9186F0E836FB: "Launchpad PPA for tomtomtom" not changed 
gpg: key 0700205DFD41A71A: "devel OBS Project <devel@s2.owncloud.com>" 10 new signatures 
gpg: key 073E051D7B2AEE37: "Launchpad PPA for OpenRazer" not changed 
gpg: key EFC71127F425E228: "Launchpad PPA for obsproject" not changed 
gpg: key EB3E94ADBE1229CF: "Microsoft (Release signing) <gpgsecurity@microsoft.com>" not changed 
gpg: key EB3E94ADBE1229CF: "Microsoft (Release signing) <gpgsecurity@microsoft.com>" not changed 
gpg: key 7C7DE49315CA99E4: "Launchpad PPA for Dupeguru" not changed 
gpg: key B00A0BD1E2C63C11: "MongoDB 5.0 Release Signing Key <packaging@mongodb.com>" not changed 
gpg: key 0700205DFD41A71A: "devel OBS Project <devel@s2.owncloud.com>" not changed 
gpg: Total number processed: 14 
gpg:              unchanged: 13 
gpg:         new signatures: 10 
[COLOR=#54ff54]**chad@X470-Gaming-Plus**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt-get update [/COLOR]
Hit:1 http://deb.volian.org/volian scar InRelease 
Hit:2 https://repo.steampowered.com/steam stable InRelease                                                           
Hit:3 https://packages.microsoft.com/repos/edge stable InRelease                                                     
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                     
Hit:5 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu jammy InRelease                                          
Hit:6 http://ppa.launchpadcontent.net/dupeguru/ppa/ubuntu jammy InRelease                                            
Hit:7 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                            
Hit:8 https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Ubuntu_22.04  InRelease 
Hit:9 http://ppa.launchpad.net/openrazer/daily/ubuntu jammy InRelease                      
Hit:10 http://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy InRelease 
Hit:11 http://ppa.launchpad.net/xtradeb/apps/ubuntu jammy InRelease 
Get:12 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB] 
Err:12 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease 
  The following signatures were invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmast
er@ubuntu.com> 
Get:13 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB] 
Err:13 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
  The following signatures were invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmast
er@ubuntu.com> 
Fetched 226 kB in 1s (177 kB/s) 
Reading package lists... Done 
W: An error occurred during the signature verification. The repository is not updated and the previous index files wi
ll be used. GPG error: http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease: The following signatures were inv
alid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
W: An error occurred during the signature verification. The repository is not updated and the previous index files wi
ll be used. GPG error: http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures were i
nvalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  The following signatures were i
nvalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  The following signatures were
 invalid: BADSIG 871920D1991BC93C Ubuntu Archive Automatic Signing Key (2018) <ftpmaster@ubuntu.com> 
W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]
```

the only way i seem to be able to properly check updates is to bypass my apt-cache-ng server (installing them with it using the proxy works fine)

---

### Post by ActionParsnip on 2023-06-06
[https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/1998865](https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/1998865)
This...maybe....

---

### Post by ActionParsnip on 2023-06-06
Fix maybe this
[https://gitlab.com/gitlab-org/gitlab-runner/-/issues/29255](https://gitlab.com/gitlab-org/gitlab-runner/-/issues/29255)

---

### Post by #&amp;thj^% on 2023-06-06
> **pqwoerituytrueiwoq said:**
> well what else could i say, it is not like i got a error...

the only way i seem to be able to properly check updates is to bypass my apt-cache-ng server (installing them with it using the proxy works fine)
Sorry pqwoerituytrueiwoq I thought it might either fix it or show why it won't.
(I was **grumpy** yesterday to be sure)
We are getting close to a small nuclear suggestion now:
```
sudo apt clean 
cd /var/lib/apt 
sudo mv lists oldlist 
sudo mkdir -p lists/partial 
sudo apt clean 
sudo apt update
```
Yep run this twice "sudo apt clean "
Have you yet filed a bug against this? or add your your self to what ActionParsnip shows. This one: [https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/1998865](https://bugs.launchpad.net/ubuntu/+source/apt-cacher-ng/+bug/1998865)

---

### Post by pqwoerituytrueiwoq on 2023-06-06
thanks for that bug report, just added myself to the count, now how do we mark this as a security issue? not being able to get security updates is a problem especially when you setup unattended upgrades and just trust it works when you tested it fight after setting up the server then a month later it stops working with is issue

---

### Post by #&amp;thj^% on 2023-06-08
Yours seem to be only related to the "backport repo"
And on Lunar there is no more backport*
For completeness all backport listed:
```
aptitude search '~Abackports ?not(~S ~i ~Abackports)'
p   cockpit                         - Web Console for Linux servers             
p   cockpit-bridge                  - Cockpit bridge server-side component      
p   cockpit-doc                     - Cockpit deployment and developer guide    
p   cockpit-networkmanager          - Cockpit user interface for networking     
p   cockpit-packagekit              - Cockpit user interface for packages       
p   cockpit-pcp                     - Cockpit PCP integration                   
p   cockpit-sosreport               - Cockpit user interface for diagnostic repo
p   cockpit-storaged                - Cockpit user interface for storage        
p   cockpit-system                  - Cockpit admin interface for a system      
p   cockpit-tests                   - Tests for Cockpit                         
p   cockpit-ws                      - Cockpit Web Service                     
```
On lunar with the flag for only "Lunar"
```
aptitude search -t $(lsb_release -sc)-backports -F '%p %v -> %V' '~U ~Abackports'

```
If your not using backports just disable for the time being.

---

