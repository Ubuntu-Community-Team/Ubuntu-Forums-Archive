---
title: "package dependencies [Resolved]"
date: 2007-05-04
forum: General Help
---

### Post by raananb on 2007-05-04
Newbe with Linux/ubuntu, on ubuntu 7.04

I am trying to install libgtk2.0-dev with Synaptic, and I get the following Synaptic messages:

libgtk2.0-dev : dependencies : libpango1.0-dev & libcairo2-dev

libpango1.0-dev : depends libcairo2-dev

libcairo2-dev : depends libcairo2 (=1.4.2-0ubuntu) but 1.4.4-1 is to be installed


Now, libcairo2 1.4.4-1 is already installed (green icon)

Where do I go from here to get libgtk2.0-dev installed?

Thanks for any help

---

### Post by jebe86 on 2007-05-04
> **raananb said:**
> Newbe with Linux/ubuntu, on ubuntu 7.04

I am trying to install libgtk2.0-dev with Synaptic, and I get the following Synaptic messages:

libgtk2.0-dev : dependencies : libpango1.0-dev & libcairo2-dev

libpango1.0-dev : depends libcairo2-dev

libcairo2-dev : depends libcairo2 (=1.4.2-0ubuntu) but 1.4.4-1 is to be installed


Now, libcairo2 1.4.4-1 is already installed (green icon)

Where do I go from here to get libgtk2.0-dev installed?

Thanks for any help

It's quite strange that Synaptic does not resolve dependencies, anyhow, have you tried installing

libcairo2-dev and all the rest by hand, i.e.

apt-get install libcairo2-dev
apt-get install all the rest ?

Hope this helps

---

### Post by raananb on 2007-05-04
Hand install gives the same result. 

sudo apt-get install libcairo2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.4-1 is to be installed
E: Broken packages

---

### Post by aysiu on 2007-05-04
Dependency problems stem from conflicting repositories.

[Get a fresh set of repositories](http://www.psychocats.net/ubuntu/sources), Reload in Synaptic, and then try again.

---

### Post by raananb on 2007-05-04
I followed the advice and refreched the repositories list.

Reload in Synaptic displays:
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release:
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

The libcairo2-dev conflict persists when the error is ignored.

---

### Post by aysiu on 2007-05-04
Sorry. This will get you the key: ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

---

### Post by raananb on 2007-05-04
Key installed and Reload OK

Installation of libcairo2-dev still impossible.  

Same error message libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.4-1 is to be installed

---

### Post by aysiu on 2007-05-04
That's odd. I'm using that exact same repositories list, and I don't get any dependency error messages: ```
sudo apt-get install libgtk2.0-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatk1.0-dev libc6-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libice-dev libpango1.0-dev libpng12-dev
  libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev linux-libc-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev libcairo2-doc libglib2.0-doc libgtk2.0-doc
  libpango1.0-doc imagemagick
The following NEW packages will be installed:
  libatk1.0-dev libc6-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libgtk2.0-dev libice-dev libpango1.0-dev
  libpng12-dev libsm-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev
  libxrender-dev linux-libc-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.9MB of archives.
After unpacking 61.6MB of additional disk space will be used.
Do you want to continue [Y/n]?
``` Can you paste the output of all these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install libgtk2.0-dev
```

---

### Post by raananb on 2007-05-04
:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 
:~$ sudo apt-get update
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_AU                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_AU          
Get:4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_AU      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_AU      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_AU
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_AU
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_AU                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Fetched 6B in 2s (2B/s)  
Reading package lists... Done
:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages
:~$

---

### Post by aysiu on 2007-05-04
How about this? ```
sudo aptitude update
sudo aptitude install libgtk2.0-dev
```

---

### Post by raananb on 2007-05-04
:~$ sudo aptitude update
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_AU                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_AU    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_AU      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_AU    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_AU                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_AU
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_AU                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_AU
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_AU             
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_AU                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_AU      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_AU
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Fetched 6B in 4s (1B/s)  
Reading package lists... Done

:~$ sudo aptitude install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libcairo2-dev 
The following NEW packages will be automatically installed:
  libatk1.0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libglib2.0-dev 
  libice-dev libpango1.0-dev libpng12-dev libsm-dev libx11-dev libxau-dev 
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev 
  libxinerama-dev libxrandr-dev libxrender-dev x11proto-core-dev 
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev 
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev 
  zlib1g-dev 
The following NEW packages will be installed:
  libatk1.0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libglib2.0-dev 
  libgtk2.0-dev libice-dev libpango1.0-dev libpng12-dev libsm-dev libx11-dev 
  libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev 
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x11proto-core-dev 
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev 
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev 
  zlib1g-dev 
0 packages upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.2MB of archives. After unpacking 45.2MB will be used.
The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.4-1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libcairo2 [1.4.4-1 (now) -> 1.4.2-0ubuntu1 (feisty)]

Score is -40

Accept this solution? [Y/n/q/?] 


This looks much better - should I accept the proposed downgrade (do I have a real choice - what is the risk) ?

I took the risk and accepted the downgrade.

libgtk2.0-dev finally installed with aptitude.

Is there anyone to look into why apt-get did not work while aptitude did?

Thanks for the help.

---

### Post by zvacet on 2007-05-04
Aptitude install packages and all dependecies wich comes with it.You have one broken package(libcairo2-dev).Go to the synaptic>edit>fix broken packages


```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by aysiu on 2007-05-04
*aptitude* tries to handle dependencies smartly. Sometimes it's smarter than *apt-get*, sometimes it's "too smart," and tries to remove a bunch of stuff you don't want removed (like your entire desktop).

---

