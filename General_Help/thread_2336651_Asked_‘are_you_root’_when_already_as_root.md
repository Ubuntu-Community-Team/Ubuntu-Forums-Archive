---
title: "Asked ‘are you root’ when already as root"
date: 2016-09-10
forum: General Help
---

### Post by hd.scania on 2016-09-10
```
root@HD-SCANIA:/home/hd_scania# apt update
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Err:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease             
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease          
Hit:5 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Hit:7 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:8 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse amd64 Packages [1680 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse Translation-en [852 B]
Get:12 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse amd64 DEP-11 Metadata [201 B]
Get:13 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse DEP-11 64x64 Icons [2699 B]
Get:14 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages [115 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-proposed/main Translation-en [41.3 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 DEP-11 Metadata [6500 B]
Get:17 http://archive.ubuntu.com/ubuntu xenial-proposed/main DEP-11 64x64 Icons [14.2 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages [57.3 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-proposed/universe Translation-en [24.7 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 DEP-11 Metadata [4536 B]
Get:21 http://archive.ubuntu.com/ubuntu xenial-proposed/universe DEP-11 64x64 Icons [50.9 kB]
E: The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@HD-SCANIA:/home/hd_scania# rm -rf /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# apt update
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Err:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease          
Hit:4 http://archive.ubuntu.com/ubuntu xenial InRelease             
Hit:5 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Hit:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:7 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:8 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
E: The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
```
root@HD-SCANIA:/home/hd_scania# rm -rf /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# mkdir /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# apt autoremove
Reading package lists... Error!
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening 
E: The package lists or status file could not be parsed or opened.
root@HD-SCANIA:/home/hd_scania# apt update
Hit:1 http://tw.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://tw.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]                                                                  
Get:3 http://tw.archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]                                                                  
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                                                                    
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]                                                   
Hit:6 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease                                               
Get:7 http://tw.archive.ubuntu.com/ubuntu xenial/universe Sources [7728 kB]                     
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [9332 B]                                                             
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main Sources [38.7 kB]                                                                
Get:10 http://tw.archive.ubuntu.com/ubuntu xenial/main Sources [868 kB]                                                                       
Get:11 http://tw.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [92.8 kB]                                                          
Get:12 http://tw.archive.ubuntu.com/ubuntu xenial-updates/main Sources [187 kB]                                                               
Get:13 http://tw.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [383 kB]                                                        
Get:14 http://tw.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [324 kB]                                                    
Get:15 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages [57.3 kB]                                                  
Get:16 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/universe Translation-en [24.7 kB]                                                  
Get:17 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 DEP-11 Metadata [4536 B]                                            
Get:18 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/universe DEP-11 64x64 Icons [50.9 kB]                                              
Get:19 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages [115 kB]                                                       
Get:20 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/main Translation-en [41.3 kB]                                                      
Get:21 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 DEP-11 Metadata [6500 B]                                                
Get:22 http://tw.archive.ubuntu.com/ubuntu xenial-proposed/main DEP-11 64x64 Icons [14.2 kB]                                                  
Fetched 10.4 MB in 2min 46s (62.3 kB/s)                                                                                                       
Reading package lists... Error!
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening 
E: The package lists or status file could not be parsed or opened.
root@HD-SCANIA:/home/hd_scania#
```
```
Errors were occured, please run Package Manager from the right-click menu or apt in terminal shell to see what are wrong.
The error messages were:
E: Opening the cache
(E: flAbsPath on /var/lib/dpkg/status was failed - realpath (2: no such files or directories)
E: Could not open file - open (2: no such files or directories)
E: Problems opening
E: The packages lists and statuses file could not be parsed or opened)
This usually means your installed packages have unmet dependencies.
```
```
root@HD-SCANIA:/home/hd_scania# cp /media/hd_scania/Arch/status /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# apt remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@HD-SCANIA:/home/hd_scania#
```
Unlike the most and many online examples, I need to state I surely log on as root. But I have no ideas to fix that my example is quite rare.

---

### Post by QIII on 2016-09-10
Hello!

Are you trying to use the terminal to update at the same time as you have a GUI updater open?

What you have posted indicates as much.  Disable the CD ROM in your sources.list, close one or the other of the software update applications and try again.

By way of warning:  logging in and running as root is not a particularly good idea.

Cheers!

---

### Post by hd.scania on 2016-09-10
I have killed any GUI updaters and thrown CD-ROM sources and restart the terminal for APT but nothing are healed.
Warning is void: my logged on session of root is stood for: logging on as root just inside the terminal shell, instead of GUI.

---

### Post by sisco311 on 2016-09-10
> **hd.scania said:**
> ```

...
root@HD-SCANIA:/home/hd_scania# rm -rf /var/lib/dpkg
...

```


Hmmm, you have deleted the /var/lib/dpkg directory, that's causing your issues. Do you have a backup to restore the directory?

---

### Post by hd.scania on 2016-09-10
In my case I dnt think I need a backup but a remade direction to recover...
```
...
root@HD-SCANIA:/home/hd_scania# rm -rf /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# mkdir /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# apt autoremove
Reading package lists... Error!
...
```

---

### Post by sisco311 on 2016-09-11
You do need a backup. dpkg and other applications store some essential files in that directory. 


If you didn't create a backup, you can use the backups created by the system:
```

mkdir -p /var/lib/dpkg/{alternatives,info,parts,triggers,updates}
cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
cp /var/backups/dpkg.statoverride.0 /var/lib/dpkg/statoverride
cp /var/backups/dpkg.status.0 /var/lib/dpkg/status

```

I don't fully understand the scope of each file in that directory, but I did a little experiment in a systemd-nspawn container and deleted (after backing up) the dpkg directory. 

After restoring the directory hierarchy and the status file I still get some warnings from dpkg/apt:
```


sisco@asrock:~$ sudo apt --reinstall install netbase
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 12.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 netbase all 5.3 [12.9 kB]
Fetched 12.9 kB in 0s (70.9 kB/s)  
dpkg: warning: files list file for package 'libquadmath0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bind9-host' missing; assuming package has no files currently installed
...

```
 
It seems that dpkg stores the list of installed files in /var/lib/dpkg/info.

In order to repopulate the info directory we need to reinstall all the packages:
```
sudo apt --reinstall install  libquadmath0 python-apt-common bind9-host ...
```


Conclusion:
Don't delete system files and make backups. 
 

Good luck!

---

### Post by hd.scania on 2016-09-11
```
root@HD-SCANIA:/home/hd_scania# cp /media/hd_scania/Arch/status /var/lib/dpkg
root@HD-SCANIA:/home/hd_scania# apt remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@HD-SCANIA:/home/hd_scania#
```
I have just fixed copying the empty &#8216;status&#8217; file to the original directory, some guys are helpless here at all.

---

