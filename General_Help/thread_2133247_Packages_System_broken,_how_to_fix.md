---
title: "Packages System broken, how to fix?"
date: 2013-04-07
forum: General Help
---

### Post by BanderSnoot on 2013-04-07
Hi,

I am running Ubuntu 12.4.

A few days ago I followed some posted directions for installing a package (it was a perl-related utility.)  The directions or something were bad, because it failed, and somehow hosed up my installed packages.

If I try to run the update manager, I get the following:[INDENT][I]**The Package system is broken**

Check is you are using third party repositories.  If so disable them, since they are a common source of problems.  Furthermore run the following command in a Terminal: apt-get install -f

Details:
[/I][/INDENT]
[INDENT]*The following packages have unmet dependencies:*[/INDENT]
[INDENT]*libwx-perl: Depends: perl (>= 5.10.1-12ubuntu2) but 5.14.2-6ubuntu2.3 is installed*[/INDENT]
[INDENT]*            Depends: perlapi-5.10.1 but it is not installed*[/INDENT]
[INDENT]*            Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.3 is installed*[/INDENT]
[INDENT]*            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed*[/INDENT]
[INDENT]*            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is installed*[/INDENT]
[INDENT]*            Depends: libwxbase2.8-0 (>= 2.8.11.0) but 2.8.12.1-6ubuntu2 is installed*[/INDENT]
[INDENT]*            Depends: libwxgtk2.8-0 (>= 2.8.11.0) but 2.8.12.1-6ubuntu2 is installed*[/INDENT]

I tried the apt-get command, but it fails complaining about other unmet dependencies.

I don't know how to fix this.

Can I re-install Ubuntu without losing my settings and apps?  Is there a "repair" option?

---

### Post by ibjsb4 on 2013-04-07
Could you post the results of:

```
sudo apt-get update
```

Using code tags

[ATTACH=CONFIG]241073[/ATTACH]

Thanks

---

### Post by BanderSnoot on 2013-04-07
Duplicate post removed.

---

### Post by ibjsb4 on 2013-04-07
Thats good.  Try an upgrade.

```
sudo apt-get upgrade
```

Any errors?

---

### Post by BanderSnoot on 2013-04-07
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update
[/FONT][/COLOR]```
Hit [http://dl.google.com]("http://dl.google.com/") stable Release.gpg
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise Release.gpg 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates Release.gpg 
Hit [http://dl.google.com]("http://dl.google.com/") stable Release 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise Release 
Hit [http://dl.google.com]("http://dl.google.com/") stable/main i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates Release 
Ign [http://dl.google.com]("http://dl.google.com/") stable/main TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse TranslationIndex 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security Release.gpg 
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise Release.gpg 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main Translation-en 
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise Release 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security Release 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse Translation-en 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe Translation-en 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted Translation-en 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe Translation-en 
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en_US 
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise/main Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main Sources
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise/main i386 Packages
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise/main TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted Translation-en
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe Translation-en
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise/main Translation-en_US
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") precise/main Translation-en
Reading package lists... Done
```

---

### Post by BanderSnoot on 2013-04-07
sudo apt-get upgrade```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libwx-perl : Depends: perlapi-5.10.1 but it is not installable
E: Unmet dependencies. Try using -f.

```

---

### Post by ibjsb4 on 2013-04-07
This will probably go right back to your first post, but give it a go.

```
sudo apt-get -f install
```

---

### Post by BanderSnoot on 2013-04-07
sudo apt-get -f install
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunity6 linux-headers-3.2.0-35 linux-headers-3.2.0-35-generic
  linux-headers-3.2.0-35-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwx-perl
The following packages will be upgraded:
  libwx-perl
1 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,674 kB of archives.
After this operation, 591 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libwx-perl:
 libwx-perl depends on perlapi-5.10.1; however:
  Package perlapi-5.10.1 is not installed.
dpkg: error processing libwx-perl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libwx-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ibjsb4 on 2013-04-07
perlapi-5.10.1 is a Lucid 10.04 package.

Please post the output of:

```
ls /etc/apt/sources.list.d
```

---

### Post by BanderSnoot on 2013-04-07
```
:~$ ls /etc/apt/software.sources.d
ls: cannot access /etc/apt/software.sources.d: No such file or directory


```

---

### Post by ibjsb4 on 2013-04-07
My bad.  Try post #9 again.

---

### Post by BanderSnoot on 2013-04-07
```


:~$ ls /etc/apt/sources.list.d
google-chrome.list  google-chrome.list.distUpgrade  google-chrome.list.save


```

I'm guessing that you are pursuing the third-party repository question?  I downloaded the package from [HERE.]("http://padre.perlide.org/download.html")  I should never have done it since it refers to release 10.10.

---

### Post by ibjsb4 on 2013-04-07
> **BanderSnoot said:**
> I'm guessing that you are pursuing the third-party repository question?  I downloaded the package from [HERE.]("http://padre.perlide.org/download.html")  I should never have done it since it refers to release 10.10.

Yep, your right.  Try this.

```
sudo dpkg --remove libwx-perl_0.9702-1_i386.deb
```

Update and upgrade if it gets removed.

---

### Post by BanderSnoot on 2013-04-07
FIXED IT!

I tried your remove command and it complained that it wanted the component, not the .deb file.  So I tried removing it by just referring to libwx-perl.  It complained and listed two dependencies, one was padre, which was where the problem started.  So I removed padre with the same command, and then there was one other dependency left, so I got brave and removed it, and then removed libwx-perl.  After that I did the upgrade command.  Well, it finished fine, and update manager started working the way it should, and the red circle with the white line through it went away.

ALL IS WELL, THANK YOU!!!!

---

### Post by ibjsb4 on 2013-04-07
Damn good show :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ibjsb4 on 2013-04-07
Hi sajal, welcome to the forums :)

You need to start your own thread in order to get the proper attention.

```
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=18812397104, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=21327537560, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=34240562184, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=21620094984, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=15982656384, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=19597773712, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=20470959632, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=29248856840, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=13486466528, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=12731329208, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=21862919920, limit=307275008
Apr  8 00:04:01 baiboo kernel: attempt to access beyond end of device
Apr  8 00:04:01 baiboo kernel: md0: rw=0, want=21393271968, limit=307275008
Apr  8 00:17:34 baiboo -- MARK --
Apr  8 00:37:34 baiboo -- MARK --
Apr  8 00:57:35 baiboo -- MARK --
Apr  8 01:17:36 baiboo -- MARK --
Apr  8 01:37:36 baiboo -- MARK --
Apr  8 01:45:22 baiboo kernel: ata1: EH complete
Apr  8 01:45:24 baiboo last message repeated 4 times
Apr  8 01:45:24 baiboo kernel: sd 0:0:0:0: SCSI error: return code = 0x08000002
Apr  8 01:45:24 baiboo kernel: sda: Current: sense key: Medium Error
Apr  8 01:45:24 baiboo kernel:     Additional sense: Unrecovered read error - auto reallocate failed
Apr  8 01:45:24 baiboo kernel: end_request: I/O error, dev sda, sector 241734327
Apr  8 01:45:24 baiboo kernel: ata1: EH complete
Apr  8 01:45:24 baiboo kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Apr  8 01:45:24 baiboo kernel: sda: Write Protect is off
Apr  8 01:45:24 baiboo kernel: SCSI device sda: drive cache: write back
Apr  8 01:45:24 baiboo kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Apr  8 01:45:24 baiboo kernel: sda: Write Protect is off
Apr  8 01:45:24 baiboo kernel: SCSI device sda: drive cache: write back
Apr  8 01:45:24 baiboo kernel: ata1: EH complete
Apr  8 01:45:24 baiboo last message repeated 4 times
Apr  8 01:45:24 baiboo kernel: sd 0:0:0:0: SCSI error: return code = 0x08000002
Apr  8 01:45:24 baiboo kernel: sda: Current: sense key: Medium Error
Apr  8 01:45:24 baiboo kernel:     Additional sense: Unrecovered read error - auto reallocate failed
Apr  8 01:45:24 baiboo kernel: end_request: I/O error, dev sda, sector 241734759
Apr  8 01:45:24 baiboo kernel: ata1: EH complete
Apr  8 01:45:24 baiboo kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Apr  8 01:45:24 baiboo kernel: sda: Write Protect is off
Apr  8 01:45:24 baiboo kernel: SCSI device sda: drive cache: write back
Apr  8 01:45:24 baiboo kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Apr  8 01:45:24 baiboo kernel: sda: Write Protect is off
Apr  8 01:45:24 baiboo kernel: SCSI device sda: drive cache: write back
```

And please use code tags :)

[ATTACH=CONFIG]241097[/ATTACH]

---

### Post by boletusatanas on 2013-11-08
Hey Guys,

I need to bring this post to life again. I am experiencing exactly the same problem of the previous user. I have the updated version of Ubuntu, the 13.10 and due to this problem I cannot use the software updater.
Ipasted some outputs from my shell. they might be useful.

Thanks in advance for the help.




sudo apt-get update
```

boletusatanas@SpartanDell:~$ sudo apt-get update 
[sudo] password for boletusatanas: 
Ign http://mirror.optimate-server.de saucy InRelease
Ign http://mirror.optimate-server.de saucy-security InRelease                  
Ign http://mirror.optimate-server.de saucy-updates InRelease                   
Ign http://dl.google.com stable InRelease                                      
Hit http://repository.spotify.com stable InRelease                             
Hit http://mirror.optimate-server.de saucy Release.gpg                         
Ign http://archive.canonical.com saucy InRelease                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirror.optimate-server.de saucy-security Release.gpg                
Hit http://mirror.optimate-server.de saucy-updates Release.gpg                 
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com saucy Release.gpg                             
Hit http://mirror.optimate-server.de saucy Release                             
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://mirror.optimate-server.de saucy-security Release                    
Hit http://archive.canonical.com saucy Release                                 
Hit http://mirror.optimate-server.de saucy-updates Release                     
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://mirror.optimate-server.de saucy/main Sources                        
Hit http://mirror.optimate-server.de saucy/restricted Sources                  
Hit http://archive.canonical.com saucy/partner Sources                         
Hit http://mirror.optimate-server.de saucy/universe Sources                    
Hit http://mirror.optimate-server.de saucy/multiverse Sources                  
Hit http://mirror.optimate-server.de saucy/main amd64 Packages                 
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://mirror.optimate-server.de saucy/restricted amd64 Packages           
Hit http://mirror.optimate-server.de saucy/universe amd64 Packages             
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://mirror.optimate-server.de saucy/multiverse amd64 Packages           
Hit http://mirror.optimate-server.de saucy/main i386 Packages                  
Hit http://mirror.optimate-server.de saucy/restricted i386 Packages            
Hit http://mirror.optimate-server.de saucy/universe i386 Packages              
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/multiverse i386 Packages            
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://mirror.optimate-server.de saucy/main Translation-en_GB              
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/main Translation-en                 
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://mirror.optimate-server.de saucy/multiverse Translation-en_GB        
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/multiverse Translation-en           
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://mirror.optimate-server.de saucy/restricted Translation-en_GB        
Hit http://mirror.optimate-server.de saucy/restricted Translation-en           
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://mirror.optimate-server.de saucy/universe Translation-en_GB          
Hit http://mirror.optimate-server.de saucy/universe Translation-en             
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://mirror.optimate-server.de saucy-security/main Sources               
Hit http://mirror.optimate-server.de saucy-security/restricted Sources         
Hit http://mirror.optimate-server.de saucy-security/universe Sources           
Hit http://mirror.optimate-server.de saucy-security/multiverse Sources         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Get:2 http://linux.dropbox.com precise Release [2.603 B]                       
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://archive.canonical.com saucy/partner Translation-en_GB               
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://mirror.optimate-server.de saucy-security/main amd64 Packages        
Hit http://mirror.optimate-server.de saucy-security/restricted amd64 Packages
Hit http://mirror.optimate-server.de saucy-security/universe amd64 Packages    
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://mirror.optimate-server.de saucy-security/multiverse amd64 Packages  
Hit http://mirror.optimate-server.de saucy-security/main i386 Packages         
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://mirror.optimate-server.de saucy-security/restricted i386 Packages   
Hit http://mirror.optimate-server.de saucy-security/universe i386 Packages     
Get:3 http://linux.dropbox.com precise/main amd64 Packages [1.148 B]           
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://archive.canonical.com saucy/partner Translation-en                  
Hit http://mirror.optimate-server.de saucy-security/multiverse i386 Packages   
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Hit http://ppa.launchpad.net saucy Release                           
Hit http://mirror.optimate-server.de saucy-security/main Translation-en        
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Get:4 http://linux.dropbox.com precise/main i386 Packages [1.148 B]
Hit http://mirror.optimate-server.de saucy-security/multiverse Translation-en
Hit http://ppa.launchpad.net saucy/main amd64 Packages               
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://mirror.optimate-server.de saucy-security/restricted Translation-en
Hit http://mirror.optimate-server.de saucy-security/universe Translation-en
Hit http://mirror.optimate-server.de saucy-updates/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://mirror.optimate-server.de saucy-updates/restricted amd64 Packages
Hit http://mirror.optimate-server.de saucy-updates/multiverse amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://mirror.optimate-server.de saucy-updates/universe amd64 Packages
Hit http://mirror.optimate-server.de saucy-updates/main i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/restricted i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/multiverse i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/universe i386 Packages
Hit http://mirror.optimate-server.de saucy-updates/main Translation-en
Hit http://mirror.optimate-server.de saucy-updates/multiverse Translation-en
Hit http://mirror.optimate-server.de saucy-updates/restricted Translation-en
Hit http://mirror.optimate-server.de saucy-updates/universe Translation-en
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://ppa.launchpad.net saucy/main amd64 Packages               
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Ign http://mirror.optimate-server.de saucy/main Translation-en_US    
Ign http://linux.dropbox.com precise/main Translation-en_GB          
Ign http://mirror.optimate-server.de saucy/multiverse Translation-en_US
Ign http://linux.dropbox.com precise/main Translation-en
Ign http://mirror.optimate-server.de saucy/restricted Translation-en_US
Ign http://mirror.optimate-server.de saucy/universe Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/main Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/main Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/multiverse Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/multiverse Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/restricted Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/restricted Translation-en_US
Ign http://mirror.optimate-server.de saucy-security/universe Translation-en_GB
Ign http://mirror.optimate-server.de saucy-security/universe Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/main Translation-en_GB
Ign http://mirror.optimate-server.de saucy-updates/main Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/multiverse Translation-en_GB
Ign http://mirror.optimate-server.de saucy-updates/multiverse Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/restricted Translation-en_GB
Ign http://linux.dropbox.com precise/main Translation-en_US           
Ign http://mirror.optimate-server.de saucy-updates/restricted Translation-en_US
Ign http://mirror.optimate-server.de saucy-updates/universe Translation-en_GB
Ign http://mirror.optimate-server.de saucy-updates/universe Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Fetched 5.388 B in 4s (1.129 B/s)
Reading package lists... Done

```



sudo apt-get upgrade
```

boletusatanas@SpartanDell:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gir1.2-rb-3.0 : Depends: librhythmbox-core8 (>= 3.0.1) but it is not installed
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.1-1ubuntu2~ppa0) but it is not installed
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not installed
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.1-1ubuntu2~ppa0) but it is not installed
E: Unmet dependencies. Try using -f.

```



sudo apt-get -f install
```

boletusatanas@SpartanDell:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  gir1.2-zeitgeist-2.0
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  librhythmbox-core8
The following NEW packages will be installed
  librhythmbox-core8
0 upgraded, 1 newly installed, 0 to remove and 38 not upgraded.
7 not fully installed or removed.
Need to get 0 B/819 kB of archives.
After this operation, 1.776 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 185000 files and directories currently installed.)
Unpacking librhythmbox-core8 (from .../librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/librhythmbox-core.so.8.0.0', which is also in package librhythmbox-core7 3.0.1-0~13.10~ppa1
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



ls /etc/apt/sources.list.d
```

boletusatanas@SpartanDell:~$ ls /etc/apt/sources.list.d
atareao-atareao-saucy.list       jacob-media-saucy.list.save
atareao-atareao-saucy.list.save  peterlevi-ppa-saucy.list
dropbox.list                     peterlevi-ppa-saucy.list.save
dropbox.list.save                videolan-stable-daily-saucy.list
google-chrome.list               videolan-stable-daily-saucy.list.save
google-chrome.list.save          webupd8team-java-saucy.list
jacob-media-saucy.list           webupd8team-java-saucy.list.save

```

---

### Post by Futant on 2013-11-08
[**[COLOR=#000000]boletusatanas[/COLOR]**]("http://ubuntuforums.org/member.php?u=1742949") -
> **ibjsb4 said:**
> 

You need to start your own thread in order to get the proper attention.



---

