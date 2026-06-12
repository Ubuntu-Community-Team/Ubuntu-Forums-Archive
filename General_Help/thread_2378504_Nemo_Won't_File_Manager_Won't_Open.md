---
title: "Nemo Won't File Manager Won't Open"
date: 2017-11-23
forum: General Help
---

### Post by ThePowerpuffGirls on 2017-11-23
I recently updated to Ubuntu 17.10, Nemo was able to install without trouble and was working, then I now it just flashes and nothing happens.

Is there a conflict with the PPAs installed:
sudo add-apt-repository ppa:webupd8team/java -y
sudo add-apt-repository ppa:jonathonf/vlc -y
sudo add-apt-repository ppa:libreoffice/ppa -y
sudo add-apt-repository ppa:openshot.developers/ppa -y
sudo add-apt-repository ppa:transmissionbt/ppa -y
sudo add-apt-repository ppa:atareao/atareao -y
sudo add-apt-repository ppa:nilarimogard/webupd8 -y
sudo add-apt-repository ppa:webupd8team/nemo3 -y
sudo add-apt-repository ppa:dawidd0811/neofetch -y

or maybe it has something to do with this when I check for updates:
```

bre@Office2:~$ sudo apt update
[sudo] password for bre: 
Hit:1 http://archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://ppa.launchpad.net/atareao/atareao/ubuntu artful InRelease         
Get:3 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]      
Ign:4 https://dl.bintray.com/resin-io/debian stable InRelease                  
Hit:5 http://archive.ubuntu.com/ubuntu artful-backports InRelease              
Get:6 http://archive.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]     
Get:7 https://dl.bintray.com/resin-io/debian stable Release [1,878 B]          
Get:8 http://archive.ubuntu.com/ubuntu artful-proposed InRelease [235 kB]      
Get:10 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [13.5 kB]
Get:11 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [44.8 kB]
Get:12 http://archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [46.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [204 B]
Get:14 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10.2 kB]
Get:15 http://archive.ubuntu.com/ubuntu artful-proposed/main amd64 DEP-11 Metadata [54.9 kB]
Get:16 http://archive.ubuntu.com/ubuntu artful-proposed/main DEP-11 64x64 Icons [27.0 kB]
Get:17 http://archive.ubuntu.com/ubuntu artful-proposed/universe amd64 DEP-11 Metadata [13.2 kB]
Hit:18 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu artful InRelease    
Ign:19 http://ppa.launchpad.net/jonathonf/vlc/ubuntu artful InRelease          
Hit:20 http://ppa.launchpad.net/libreoffice/ppa/ubuntu artful InRelease
Hit:21 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu artful InRelease   
Ign:22 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu artful InRelease
Ign:23 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu artful InRelease
Hit:24 http://ppa.launchpad.net/webupd8team/java/ubuntu artful InRelease
Ign:25 http://ppa.launchpad.net/webupd8team/nemo/ubuntu artful InRelease       
Hit:26 http://ppa.launchpad.net/webupd8team/nemo3/ubuntu artful InRelease
Err:27 http://ppa.launchpad.net/jonathonf/vlc/ubuntu artful Release            
  404  Not Found
Err:28 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu artful Release
  404  Not Found
Err:29 http://ppa.launchpad.net/transmissionbt/ppa/ubuntu artful Release
  404  Not Found
Err:30 http://ppa.launchpad.net/webupd8team/nemo/ubuntu artful Release
  404  Not Found
Reading package lists... Done
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
E: The repository 'http://ppa.launchpad.net/jonathonf/vlc/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/openshot.developers/ppa/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/transmissionbt/ppa/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webupd8team/nemo/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7

```

---

### Post by ThePowerpuffGirls on 2017-11-23
Update, I reinstalled and this time didn't install some PPAs.
The only PPAs installed are:
resin-io/debian
nilarimogard/webupd8
webupd8team/java
dawidd0811/neofetch
atareao/atareao

Some errors went away that I seen with updates, instead something new appears.Two packages will be held back when trying to update:
```

bre@Office2:~$ sudo apt update
[sudo] password for bre: 
Hit:1 http://ca.archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://archive.ubuntu.com/ubuntu artful InRelease                        
Get:3 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]    
Hit:4 http://ppa.launchpad.net/atareao/atareao/ubuntu artful InRelease         
Hit:5 http://ca.archive.ubuntu.com/ubuntu artful-updates InRelease             
Hit:6 http://ca.archive.ubuntu.com/ubuntu artful-backports InRelease           
Ign:7 https://dl.bintray.com/resin-io/debian stable InRelease                  
Get:8 http://ca.archive.ubuntu.com/ubuntu artful-proposed InRelease [235 kB]   
Hit:9 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu artful InRelease     
Get:10 https://dl.bintray.com/resin-io/debian stable Release [1,878 B]         
Hit:11 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu artful InRelease   
Hit:13 http://ppa.launchpad.net/webupd8team/java/ubuntu artful InRelease      
Fetched 315 kB in 1s (257 kB/s)                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
bre@Office2:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  fwupdate libfwup1
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.


```

---

### Post by ThePowerpuffGirls on 2017-11-23
Update:
I just manually installed fwupdate and the errors went away.
Nemo still works, so one of the PPAs was brkeaing it somehow, either LibreOffice or VLC, not sure which one but will do a test install tomorrow and see which one or if both of them are responsible.
EVerything appears to be working good now.

---

### Post by again? on 2017-11-23
Nemo from ppa:webupd8team/nemo3 recently failed to work for me on 17.04.
Purged the ppa and nemo runs fine.
Better off using nemo from default Ubuntu repositories now Ubuntu has started using gnome-shell.

---

### Post by ThePowerpuffGirls on 2017-11-23
I haven't tried just removing the PPA for Nemo, I will try that and then will install VLC test and then LibreOffice.

---

### Post by ThePowerpuffGirls on 2017-11-24
It appears that it is the Nemo PPA. I installed oth LibreOffice and VLC and it didn't break this time.

---

