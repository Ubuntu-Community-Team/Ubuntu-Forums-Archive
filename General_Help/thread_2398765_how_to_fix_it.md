---
title: "how to fix it ?"
date: 2018-08-17
forum: General Help
---

### Post by androidzip on 2018-08-17
gurudecode@gurudecode:~$ sudo apt-get update
[sudo] password for gurudecode: 
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper InRelease                        
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper Release                          
  404  Not Found [IP: 91.189.88.152 80]
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:6 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:7 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:8 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Ign:9 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) bionic InRelease           
Hit:10 [http://ppa.launchpad.net/noobslab/macbuntu/ubuntu](http://ppa.launchpad.net/noobslab/macbuntu/ubuntu) bionic InRelease      
Err:11 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) bionic Release            
  404  Not Found [IP: 91.189.95.83 80]
Hit:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease             
Reading package lists... Done         
E: The repository 'http://archive.ubuntu.com/ubuntu dapper Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/noobslab/apps/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by oldos2er on 2018-08-17
Remove the noobslab PPA, since it doesn't exist for bionic. Also remove the "dapper" sources because they are incredibly out of date.

---

### Post by androidzip on 2018-08-17
how to remove  noobslab PPA ,dapper

---

### Post by deadflowr on 2018-08-17
Open the program Software and Updates and go to the section Other Software.
scroll down to find the noobslab apps ppa listing and uncheck it. Make sure you double check it's the apps ppa and not the macbuntu theme ppa.

(double points if you can find the dapper listed there as well., if dapper not list, maybe look in the section Updates. Perhaps it's listed there as one of the update repositories.)

If you cannot find any listing in Software and Updates for dapper, then you'll need to edit out the entries from the sources.list file.
You can invoke the source editing command with
```
sudo apt edit-sources
```
(The default editor should be nano, so when you edit the entry, when done pres ctrl + X to save and exit; ctrl+ X, then press Y to confirm the changes then press enter to save the file as is.)

Then try re-running the update command you ran in post #1.

---

### Post by androidzip on 2018-08-18
not solved .gave any script which solve error automatically .

---

### Post by deadflowr on 2018-08-18
> **androidzip said:**
> not solved .gave any script which solve error automatically .

There really isn't any generic script to do this. Any script would be customized as every error of this type is unique and would require some adjustments to it.
Post back all you have done, or tried to do.

---

### Post by oldos2er on 2018-08-18
> **androidzip said:**
> how to remove  noobslab PPA ,dapper

Please show all the text output from ```
sudo apt update
```

---

