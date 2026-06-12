---
title: "Java Problem, I think..."
date: 2007-11-07
forum: General Help
---

### Post by DanielLloyd on 2007-11-07
Hi everyone,

I'm a bit stuck, I've installed OpenFOAM but when I try to run it I get the following error. I think it has something to do with java but I dont really have a clue. 

I'd really appreciate any help as this is for work and I'm running out of time pretty quick.

Thanks

```
daniel@daniel-laptop:~/OpenFOAM/OpenFOAM-1.4.1/bin$ FoamX
Starting NameServer with inet:daniel-laptop:1234 ...
Starting FoamX Host Browser with inet:daniel-laptop:1234 ...
/*---------------------------------------------------------------------------*\
| ========= | |
| \\ / F ield | OpenFOAM: The Open Source CFD Toolbox |
| \\ / O peration | Version: 1.4.1 |
| \\ / A nd | Web: http://www.openfoam.org |
| \\/ M anipulation | |
\*---------------------------------------------------------------------------*/

Exec : FoamXHostBrowser 
Date : Nov 07 2007
Time : 11:31:22
Host : daniel-laptop
PID : 18959
Root : 
Case : 
Nprocs : 1
HostBrowser running.....
Setting LANG to en_EN
Using jar /home/daniel/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/l ib/FoamX.jar
Using jar /home/daniel/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/l ib/jlfgr-1_0.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
at java.awt.GraphicsEnvironment.getLocalGraphicsEnvir onment(libgcj.so.81)
at java.awt.Window.<init>(libgcj.so.81)
at java.awt.Frame.<init>(libgcj.so.81)
at javax.swing.JFrame.<init>(libgcj.so.81)
at FoamX.App.<init>(App.java:196)
at FoamX.App.main(App.java:184)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
at java.lang.Runtime._load(libgcj.so.81)
at java.lang.Runtime.loadLibrary(libgcj.so.81)
at java.lang.System.loadLibrary(libgcj.so.81)
at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.s o.81)
at java.lang.Class.initializeClass(libgcj.so.81)
at java.lang.Class.forName(libgcj.so.81)
at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
...6 more
Killed
runFoamXHB : cleanup
runFoamXHB: Killing name server nsd(pid 18957).
daniel@daniel-laptop:~/OpenFOAM/OpenFOAM-1.4.1/bin$ 
```

---

### Post by taurus on 2007-11-07
Have you installed the latest version of Sun's java?  What's the output of this command from a terminal?

```
java -version
```

---

### Post by jespdj on 2007-11-07
From the error message, it looks like you are using GNU Java. GNU Java is an incomplete and slow, but free, version of Java 1.4.

Install the latest version of Sun's Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
Then, make sure that Sun's Java is the default Java that's used:
```
sudo update-alternatives --config java
```

---

### Post by DanielLloyd on 2007-11-07
I have version 1.4.2_05-b04 according to the java -version command.
I managed to get OpenFoam to work once, when I closed it and tried to run it again it gave the above error. I changed OpenFOAM to use Ubuntu's java, rather than the one it came with OpenFOAM as it was causing problems.

I currently cant get on the net with my laptop so I'll have to get the Sun java files when I get home.

---

### Post by DanielLloyd on 2007-11-07
I tried the command again and it said the package is unavailable. I then tried to add the java console via the add/remove programme app but it says I have conflicting software. How do I get round this or work out what its conflicting with?

---

### Post by taurus on 2007-11-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by DanielLloyd on 2007-11-07
I dont know if that run properly but this is what I got back.

```

daniel@daniel-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updatdaniel@daniel-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
es main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by taurus on 2007-11-07
You don't have a whole lot of repos in your /etc/apt/sources.list.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place the # in front of the first line, cdrom, to comment it out so it won't keep asking you to insert the CD.

Then, remove the # in front of all the lines that start with deb & deb-src.  Save it and run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by DanielLloyd on 2007-11-07
Seemed to install ok, though it still says that the java version is 1.4.2_05

```

daniel@daniel-laptop:~$ sudo apt-get update
Get: 1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_GB           
Get: 2 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]    
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_GB       
Get: 3 http://archive.canonical.com gutsy Release.gpg [191B]         
Ign http://archive.canonical.com gutsy/partner Translation-en_GB               
Get: 4 http://gb.archive.ubuntu.com gutsy Release.gpg [191B]         
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_GB     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_GB       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_GB   
Hit http://security.ubuntu.com gutsy-security Release                
Get: 5 http://archive.canonical.com gutsy Release [6998B]            
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_GB   
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_GB
Get: 6 http://archive.ubuntu.com gutsy Release.gpg [191B]            
Hit http://archive.ubuntu.com gutsy/multiverse Translation-en_GB     
Hit http://archive.ubuntu.com gutsy/universe Translation-en_GB       
Hit http://archive.ubuntu.com gutsy-updates Release                            
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://archive.ubuntu.com gutsy Release                                    
Get: 7 http://gb.archive.ubuntu.com gutsy/main Translation-en_GB [21.3kB]
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Get: 8 http://security.ubuntu.com gutsy-security/main Sources [3108B]          
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages                
Hit http://archive.ubuntu.com gutsy-updates/main Packages                      
Ign http://archive.canonical.com gutsy/partner Packages                        
Hit http://archive.ubuntu.com gutsy-updates/universe Packages                  
Get: 9 http://security.ubuntu.com gutsy-security/restricted Sources [14B]      
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Get: 10 http://security.ubuntu.com gutsy-security/universe Sources [1539B]     
Get: 11 http://gb.archive.ubuntu.com gutsy/restricted Translation-en_GB [2395B]
Get: 12 http://gb.archive.ubuntu.com gutsy/universe Translation-en_GB [4405B]  
Get: 13 http://security.ubuntu.com gutsy-security/multiverse Packages [599B]   
Get: 14 http://security.ubuntu.com gutsy-security/multiverse Sources [14B]     
Hit http://archive.ubuntu.com gutsy/multiverse Packages                        
Get: 15 http://gb.archive.ubuntu.com gutsy/multiverse Translation-en_GB [8133B]
Ign http://archive.canonical.com gutsy/partner Sources                         
Hit http://archive.ubuntu.com gutsy/universe Packages                        
Get: 16 http://gb.archive.ubuntu.com gutsy-updates Release.gpg [191B]        
Ign http://gb.archive.ubuntu.com gutsy-updates/main Translation-en_GB        
Ign http://gb.archive.ubuntu.com gutsy-updates/restricted Translation-en_GB  
Ign http://gb.archive.ubuntu.com gutsy-updates/universe Translation-en_GB    
Ign http://gb.archive.ubuntu.com gutsy-updates/multiverse Translation-en_GB  
Get: 17 http://gb.archive.ubuntu.com gutsy-backports Release.gpg [191B]      
Ign http://gb.archive.ubuntu.com gutsy-backports/main Translation-en_GB      
Ign http://gb.archive.ubuntu.com gutsy-backports/restricted Translation-en_GB
Get: 18 http://archive.canonical.com gutsy/partner Packages [676B]            
Ign http://gb.archive.ubuntu.com gutsy-backports/universe Translation-en_GB   
Ign http://gb.archive.ubuntu.com gutsy-backports/multiverse Translation-en_GB
Get: 19 http://gb.archive.ubuntu.com gutsy Release [65.9kB] 
Get: 20 http://archive.canonical.com gutsy/partner Sources [355B]         
Get: 21 http://gb.archive.ubuntu.com gutsy-updates Release [51.2kB]
Get: 22 http://gb.archive.ubuntu.com gutsy-backports Release [37.0kB]
Get: 23 http://gb.archive.ubuntu.com gutsy/main Packages [1075kB]
Get: 24 http://gb.archive.ubuntu.com gutsy/restricted Packages [7664B]
Get: 25 http://gb.archive.ubuntu.com gutsy/main Sources [306kB]
Get: 26 http://gb.archive.ubuntu.com gutsy/restricted Sources [2120B]
Get: 27 http://gb.archive.ubuntu.com gutsy/universe Packages [4065kB]
Get: 28 http://gb.archive.ubuntu.com gutsy/universe Sources [1226kB]           
Get: 29 http://gb.archive.ubuntu.com gutsy/multiverse Packages [158kB]         
Get: 30 http://gb.archive.ubuntu.com gutsy/multiverse Sources [56.8kB]         
Get: 31 http://gb.archive.ubuntu.com gutsy-updates/main Packages [15.7kB]      
Get: 32 http://gb.archive.ubuntu.com gutsy-updates/restricted Packages [14B]   
Get: 33 http://gb.archive.ubuntu.com gutsy-updates/main Sources [4924B]        
Get: 34 http://gb.archive.ubuntu.com gutsy-updates/restricted Sources [14B]    
Get: 35 http://gb.archive.ubuntu.com gutsy-updates/universe Packages [9282B]   
Get: 36 http://gb.archive.ubuntu.com gutsy-updates/universe Sources [2068B]    
Get: 37 http://gb.archive.ubuntu.com gutsy-updates/multiverse Packages [599B]  
Get: 38 http://gb.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]    
Get: 39 http://gb.archive.ubuntu.com gutsy-backports/main Packages [3054B]     
Get: 40 http://gb.archive.ubuntu.com gutsy-backports/restricted Packages [14B] 
Get: 41 http://gb.archive.ubuntu.com gutsy-backports/universe Packages [1718B] 
Get: 42 http://gb.archive.ubuntu.com gutsy-backports/multiverse Packages [14B] 
Get: 43 http://gb.archive.ubuntu.com gutsy-backports/main Sources [1470B]      
Get: 44 http://gb.archive.ubuntu.com gutsy-backports/restricted Sources [14B]  
Get: 45 http://gb.archive.ubuntu.com gutsy-backports/universe Sources [1407B]  
Get: 46 http://gb.archive.ubuntu.com gutsy-backports/multiverse Sources [14B]  
Fetched 7141kB in 9s (752kB/s)                                                 
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com gutsy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com gutsy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
daniel@daniel-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base java-common libstdc++5 odbcinst1debian1 unixodbc
Suggested packages:
  equivs binfmt-support sun-java6-fonts libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed
  gcc-3.3-base java-common libstdc++5 odbcinst1debian1 sun-java6-bin
  sun-java6-jre sun-java6-plugin unixodbc
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.6MB of archives.
After unpacking 96.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com gutsy/main java-common 0.26ubuntu1 [77.1kB]
Get: 2 http://gb.archive.ubuntu.com gutsy/main odbcinst1debian1 2.2.11-16 [67.3kB]
Get: 3 http://gb.archive.ubuntu.com gutsy/main unixodbc 2.2.11-16 [297kB]
Get: 4 http://gb.archive.ubuntu.com gutsy/main gcc-3.3-base 1:3.3.6-15ubuntu2 [151kB]
Get: 5 http://gb.archive.ubuntu.com gutsy/main libstdc++5 1:3.3.6-15ubuntu2 [296kB]
Get: 6 http://gb.archive.ubuntu.com gutsy/multiverse sun-java6-bin 6-03-0ubuntu2 [26.4MB]
Get: 7 http://gb.archive.ubuntu.com gutsy/multiverse sun-java6-jre 6-03-0ubuntu2 [6327kB]
Get: 8 http://gb.archive.ubuntu.com gutsy/multiverse sun-java6-plugin 6-03-0ubuntu2 [1598B]
Fetched 33.6MB in 38s (869kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 88942 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.26ubuntu1_all.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16_i386.deb) ...
Selecting previously deselected package gcc-3.3-base.
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu2_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu2_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-03-0ubuntu2_i386.deb) ...
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Setting up sun-java6-bin (6-03-0ubuntu2) ...
No theme index file in '/usr/share/icons/sun-java6.png'.
If you really want to create an icon cache here, use --ignore-theme-index.

Setting up sun-java6-plugin (6-03-0ubuntu2) ...

Setting up sun-java6-jre (6-03-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

and this is the java -version

```

daniel@daniel-laptop:~$ java -version
java version "1.4.2_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_05-b04)
Java HotSpot(TM) Client VM (build 1.4.2_05-b04, mixed mode)
daniel@daniel-laptop:~$ 

```

---

### Post by taurus on 2007-11-07
Do you see the new one on the list after running this command from a terminal?

```
sudo update-alternatives --config java
```
Make sure it is the default version.

---

### Post by DanielLloyd on 2007-11-07
I just run the update, it installed ok, then I ran openFOAM and it seems to have worked.

Thanks so much Taurus

---

