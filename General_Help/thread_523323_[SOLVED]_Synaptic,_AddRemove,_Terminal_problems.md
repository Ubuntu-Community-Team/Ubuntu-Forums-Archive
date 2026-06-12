---
title: "[SOLVED] Synaptic, Add/Remove, Terminal problems"
date: 2007-08-11
forum: General Help
---

### Post by CRill130 on 2007-08-11
Just installed fiesty (dual boot) on hp laptop with what i thought was no problems, but I can't install any programs or codecs. Add/remove tells me there is a conflict and to use synaptic. Synaptic tells me the files are uninstallable. I tried the terminal with instructions found online with no result. I guess I should mention that I am trying to load the gstreamer codecs (bad and ugly). I tried loading other programs to see if it was just the codecs but I can't seem to load anything. Any help would be greatly apprieciated. As a new ubuntu user I'm sure I left out some important piece(s) of info. Help me help you help me....

thanks

---

### Post by aysiu on 2007-08-11
You can't use two package managing programs at once.

So if you have Synaptic open, you can't use Add/Remove. If you have Add/Remove open, you can't *apt-get install* anything.

Can you close Synaptic and Add/Remove, open a terminal, paste in these commands, and then paste back here the output? ```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
cat /etc/apt/sources.list
```

---

### Post by CRill130 on 2007-08-11
Here are the results:

chris@chris-laptop:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages [1307kB]
99% [4 Packages gzip 0] [Waiting for headers]             
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  Sub-process gzip returned an error code (1)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) free/non-free Packages
  404 Not Found [IP: 193.34.16.167 80]
Fetched 4B in 0s (4B/s)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://packages.medibuntu.org/feisty/dists/free/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/feisty/dists/free/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
chris@chris-laptop:~$ sudo apt-get install ubuntu-restricted-extras
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
  ubuntu-restricted-extras: Depends: gstreamer0.10-plugins-ugly but it is not going to be installed
                            Depends: sun-java6-plugin but it is not going to be installed
E: Broken packages
chris@chris-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/feisty](http://packages.medibuntu.org/feisty) free non-free
chris@chris-laptop:~$

---

### Post by aysiu on 2007-08-11
Well the 404 error for Medibuntu has to do with a missing space, but the gzip error may be something weird with the US repositories right now.

Try [this](http://psychocats.net/ubuntu/sources#editfile) and [this](http://psychocats.net/ubuntu/sources#feisty); then run these commands again: ```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
``` It's **imperative** that you copy and paste instead of retyping.

---

### Post by CRill130 on 2007-08-11
Got and OK when I tried the first (add key).

When I tried the second (update list) I got:

bash: deb-src: command not found

---

### Post by aysiu on 2007-08-11
*deb-src* isn't one of the commands you're supposed to be pasting in.

You're just backing up the /etc/apt/sources.list file, editing it, and then pasting in a new set of sources.

The commands are:
*mv* (move this file)
*gedit* (open this file in a text editor)

Those are the only two commands. Then you paste a huge chunk into the open text editor, save the text editor and close it.

Finally, you'll use the *apt-get* command.

Nowhere in the instructions are you asked to use a command that is or contains *deb-src*.

Please post the **entire** output of the terminal, not just that one part about the command not being found.

---

### Post by CRill130 on 2007-08-12
Ok I think I understand now what you suggested. Being new to non-windows and not having used any command line type interface for a decade or so I had just copied and pasted everything into the terminal (woops). Here are the results after pulling my head out....```
chris@chris-laptop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backupPassword:
chris@chris-laptop:~$ gksudo gedit /etc/apt/sources.list
chris@chris-laptop:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:3 http://medibuntu.sos-sts.com feisty Release.gpg [189B]         
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US                 
Get:4 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US    
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US
Get:5 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US          
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US  
Get:6 http://medibuntu.sos-sts.com feisty Release [2195B]            
Get:7 http://archive.canonical.com feisty-commercial Release [4878B]           
Get:8 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Hit http://security.ubuntu.com feisty-security/main Packages                   
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:9 http://archive.ubuntu.com feisty Release [57.2kB]                        
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources               
Hit http://security.ubuntu.com feisty-security/restricted Sources         
Get:10 http://archive.canonical.com feisty-commercial/main Packages [2045B]
Ign http://medibuntu.sos-sts.com feisty/free Packages                          
Hit http://security.ubuntu.com feisty-security/universe Packages            
Hit http://security.ubuntu.com feisty-security/universe Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources  
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Get:11 http://archive.ubuntu.com feisty-updates Release [32.4kB]
Get:12 http://medibuntu.sos-sts.com feisty/free Packages [5483B]
Get:13 http://archive.ubuntu.com feisty-backports Release [44.6kB]
Get:14 http://archive.ubuntu.com feisty/main Packages [1007kB]                 
Get:15 http://medibuntu.sos-sts.com feisty/non-free Packages [2849B]
Get:16 http://medibuntu.sos-sts.com feisty/free Sources [1804B]
Get:17 http://medibuntu.sos-sts.com feisty/non-free Sources [1362B]            
Get:18 http://archive.ubuntu.com feisty/restricted Packages [7628B]
Get:19 http://archive.ubuntu.com feisty/main Sources [293kB]
Get:20 http://archive.ubuntu.com feisty/restricted Sources [1710B]
Get:21 http://archive.ubuntu.com feisty/universe Packages [3754kB]
Get:22 http://archive.ubuntu.com feisty/universe Sources [1131kB]              
Get:23 http://archive.ubuntu.com feisty/multiverse Packages [148kB]            
Get:24 http://archive.ubuntu.com feisty/multiverse Sources [51.3kB]            
Get:25 http://archive.ubuntu.com feisty-updates/main Packages [54.7kB]         
Get:26 http://archive.ubuntu.com feisty-updates/restricted Packages [14B]      
Get:27 http://archive.ubuntu.com feisty-updates/main Sources [19.2kB]          
Get:28 http://archive.ubuntu.com feisty-updates/restricted Sources [14B]       
Get:29 http://archive.ubuntu.com feisty-backports/main Packages [17.4kB]       
Get:30 http://archive.ubuntu.com feisty-backports/restricted Packages [14B]    
Get:31 http://archive.ubuntu.com feisty-backports/universe Packages [34.6kB]   
Get:32 http://archive.ubuntu.com feisty-backports/multiverse Packages [930B]   
Fetched 6677kB in 13s (489kB/s)                                                
Reading package lists... Done
chris@chris-laptop:~$ 


```

---

### Post by CRill130 on 2007-08-12
AH HA!!!
I think I have had success. I must have over-thought the difficulty of ubuntu. Why was I stuck to windows for so long.....
```
chris@chris-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libdvdread3
  libid3tag0 liblame0 libltdl3 libmad0 libmpeg2-4 libsidplay1 msttcorefonts
  odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin unixodbc
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs equivs libdvdcss2 debhelper
  fakeroot sidplay-base xsidplay sun-java6-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libdvdread3
  libid3tag0 liblame0 libltdl3 libmad0 libmpeg2-4 libsidplay1 msttcorefonts
  odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin
  ubuntu-restricted-extras unixodbc
0 upgraded, 20 newly installed, 0 to remove and 8 not upgraded.
Need to get 34.0MB of archives.
After unpacking 97.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com feisty/main java-common 0.25ubuntu2 [76.9kB]
Get:2 http://archive.ubuntu.com feisty/main libltdl3 1.5.22-4 [168kB]
Get:3 http://archive.ubuntu.com feisty/main odbcinst1debian1 2.2.11-13 [64.1kB]
Get:4 http://archive.ubuntu.com feisty/main unixodbc 2.2.11-13 [269kB]
Get:5 http://archive.ubuntu.com feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:6 http://archive.ubuntu.com feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]
Get:7 http://archive.ubuntu.com feisty/universe cabextract 1.2-2 [53.9kB]      
Get:8 http://archive.ubuntu.com feisty/multiverse flashplugin-nonfree 9.0.31.0.2ubuntu1 [15.4kB]
Get:9 http://archive.ubuntu.com feisty/universe liba52-0.7.4 0.7.4-7 [26.4kB]  
Get:10 http://archive.ubuntu.com feisty/universe libdvdread3 0.9.7-2ubuntu1 [57.7kB]
Get:11 http://archive.ubuntu.com feisty/main libid3tag0 0.15.1b-8 [34.9kB]     
Get:12 http://archive.ubuntu.com feisty/main libmad0 0.15.1b-2.1 [76.9kB]      
Get:13 http://archive.ubuntu.com feisty/universe libmpeg2-4 0.4.1-1 [64.1kB]   
Get:14 http://archive.ubuntu.com feisty/universe libsidplay1 1.36.59-4 [65.9kB]
Get:15 http://archive.ubuntu.com feisty/universe gstreamer0.10-plugins-ugly 0.10.5-0ubuntu2 [207kB]
Get:16 http://archive.ubuntu.com feisty/multiverse liblame0 3.96.1-2ubuntu1 [190kB]
Get:17 http://archive.ubuntu.com feisty/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.5-2 [40.0kB]
Get:18 http://archive.ubuntu.com feisty/multiverse msttcorefonts 1.8ubuntu1 [35.0kB]
Get:19 http://archive.ubuntu.com feisty/multiverse sun-java6-plugin 6-00-2ubuntu2 [1392B]
Get:20 http://archive.ubuntu.com feisty/multiverse ubuntu-restricted-extras 2.2 [1920B]
Fetched 34.0MB in 40s (838kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 104704 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu2_all.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-13_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-13_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package cabextract.
Unpacking cabextract (from .../cabextract_1.2-2_i386.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.31.0.2ubuntu1_i386.deb) ...
Selecting previously deselected package liba52-0.7.4.
Unpacking liba52-0.7.4 (from .../liba52-0.7.4_0.7.4-7_i386.deb) ...
Selecting previously deselected package libdvdread3.
Unpacking libdvdread3 (from .../libdvdread3_0.9.7-2ubuntu1_i386.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-8_i386.deb) ...
Selecting previously deselected package libmad0.
Unpacking libmad0 (from .../libmad0_0.15.1b-2.1_i386.deb) ...
Selecting previously deselected package libmpeg2-4.
Unpacking libmpeg2-4 (from .../libmpeg2-4_0.4.1-1_i386.deb) ...
Selecting previously deselected package libsidplay1.
Unpacking libsidplay1 (from .../libsidplay1_1.36.59-4_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly.
Unpacking gstreamer0.10-plugins-ugly (from .../gstreamer0.10-plugins-ugly_0.10.5-0ubuntu2_i386.deb) ...
Selecting previously deselected package liblame0.
Unpacking liblame0 (from .../liblame0_3.96.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly-multiverse.
Unpacking gstreamer0.10-plugins-ugly-multiverse (from .../gstreamer0.10-plugins-ugly-multiverse_0.10.5-2_i386.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_1.8ubuntu1_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_2.2_i386.deb) ...
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Setting up cabextract (1.2-2) ...
Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--08:58:10--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.34.70
Connecting to fpdownload.macromedia.com|72.246.34.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,608,602 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  583.78 KB/s
   50K .......... .......... .......... .......... ..........  3%  876.98 KB/s
  100K .......... .......... .......... .......... ..........  5%  782.72 KB/s
  150K .......... .......... .......... .......... ..........  7%  889.78 KB/s
  200K .......... .......... .......... .......... ..........  9%  766.99 KB/s
  250K .......... .......... .......... .......... .......... 11%  859.86 KB/s
  300K .......... .......... .......... .......... .......... 13%  825.94 KB/s
  350K .......... .......... .......... .......... .......... 15%  887.22 KB/s
  400K .......... .......... .......... .......... .......... 17%  792.96 KB/s
  450K .......... .......... .......... .......... .......... 19%  818.82 KB/s
  500K .......... .......... .......... .......... .......... 21%  904.39 KB/s
  550K .......... .......... .......... .......... .......... 23%  787.17 KB/s
  600K .......... .......... .......... .......... .......... 25%  828.24 KB/s
  650K .......... .......... .......... .......... .......... 27%  844.32 KB/s
  700K .......... .......... .......... .......... .......... 29%  781.70 KB/s
  750K .......... .......... .......... .......... .......... 31%  890.17 KB/s
  800K .......... .......... .......... .......... .......... 33%  834.15 KB/s
  850K .......... .......... .......... .......... .......... 35%  831.48 KB/s
  900K .......... .......... .......... .......... .......... 37%  824.09 KB/s
  950K .......... .......... .......... .......... .......... 39%  773.18 KB/s
 1000K .......... .......... .......... .......... .......... 41%  911.63 KB/s
 1050K .......... .......... .......... .......... .......... 43%  781.76 KB/s
 1100K .......... .......... .......... .......... .......... 45%  884.02 KB/s
 1150K .......... .......... .......... .......... .......... 47%  791.58 KB/s
 1200K .......... .......... .......... .......... .......... 49%  822.23 KB/s
 1250K .......... .......... .......... .......... .......... 51%  839.83 KB/s
 1300K .......... .......... .......... .......... .......... 52%  854.91 KB/s
 1350K .......... .......... .......... .......... .......... 54%  811.49 KB/s
 1400K .......... .......... .......... .......... .......... 56%  826.76 KB/s
 1450K .......... .......... .......... .......... .......... 58%  828.62 KB/s
 1500K .......... .......... .......... .......... .......... 60%  848.56 KB/s
 1550K .......... .......... .......... .......... .......... 62%  826.88 KB/s
 1600K .......... .......... .......... .......... .......... 64%  823.64 KB/s
 1650K .......... .......... .......... .......... .......... 66%  788.28 KB/s
 1700K .......... .......... .......... .......... .......... 68%  836.32 KB/s
 1750K .......... .......... .......... .......... .......... 70%  890.17 KB/s
 1800K .......... .......... .......... .......... .......... 72%  839.52 KB/s
 1850K .......... .......... .......... .......... .......... 74%  820.78 KB/s
 1900K .......... .......... .......... .......... .......... 76%  784.09 KB/s
 1950K .......... .......... .......... .......... .......... 78%  848.53 KB/s
 2000K .......... .......... .......... .......... .......... 80%  827.27 KB/s
 2050K .......... .......... .......... .......... .......... 82%  874.73 KB/s
 2100K .......... .......... .......... .......... .......... 84%  791.06 KB/s
 2150K .......... .......... .......... .......... .......... 86%  837.52 KB/s
 2200K .......... .......... .......... .......... .......... 88%  817.48 KB/s
 2250K .......... .......... .......... .......... .......... 90%  830.70 KB/s
 2300K .......... .......... .......... .......... .......... 92%  891.92 KB/s
 2350K .......... .......... .......... .......... .......... 94%  797.14 KB/s
 2400K .......... .......... .......... .......... .......... 96%  830.89 KB/s
 2450K .......... .......... .......... .......... .......... 98%  810.60 KB/s
 2500K .......... .......... .......... .......... .......   100%  877.09 KB/s

08:58:13 (824.40 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [2608602/2608602]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Setting up liba52-0.7.4 (0.7.4-7) ...

Setting up libdvdread3 (0.9.7-2ubuntu1) ...

Setting up libid3tag0 (0.15.1b-8) ...

Setting up libmad0 (0.15.1b-2.1) ...

Setting up libmpeg2-4 (0.4.1-1) ...

Setting up libsidplay1 (1.36.59-4) ...
Setting up gstreamer0.10-plugins-ugly (0.10.5-0ubuntu2) ...
Setting up liblame0 (3.96.1-2ubuntu1) ...

Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.5-2) ...
Setting up msttcorefonts (1.8ubuntu1) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--08:58:21--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      203.05K/s             

08:58:23 (202.47 KB/s) - `./andale32.exe' saved [198384/198384]

--08:58:23--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      222.48K/s             

08:58:24 (221.89 KB/s) - `./arialb32.exe' saved [168176/168176]

--08:58:24--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208      440.87K/s             

08:58:25 (439.98 KB/s) - `./arial32.exe' saved [554208/554208]

--08:58:25--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
           => `./comic32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      267.00K/s             

08:58:27 (266.38 KB/s) - `./comic32.exe' saved [246008/246008]

--08:58:27--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      448.54K/s             

08:58:28 (447.47 KB/s) - `./courie32.exe' saved [646368/646368]

--08:58:28--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      352.87K/s             

08:58:30 (352.04 KB/s) - `./georgi32.exe' saved [392440/392440]

--08:58:30--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      222.28K/s             

08:58:31 (222.15 KB/s) - `./impact32.exe' saved [173288/173288]

--08:58:31--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[===============================================>] 661,728      465.81K/s             

08:58:32 (464.64 KB/s) - `./times32.exe' saved [661728/661728]

--08:58:32--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[=====================================================================>] 357,200      327.48K/s             

08:58:34 (326.62 KB/s) - `./trebuc32.exe' saved [357200/357200]

--08:58:34--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[==========================================================================>] 351,992      333.85K/s             

08:58:35 (332.75 KB/s) - `./verdan32.exe' saved [351992/351992]

--08:58:35--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[==========================================================================>] 185,072      239.39K/s             

08:58:36 (238.67 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-plugin (6-00-2ubuntu2) ...

Setting up ubuntu-restricted-extras (2.2) ...
chris@chris-laptop:~$ 


```

---

### Post by aysiu on 2007-08-12
Yeah, you're all set.

---

