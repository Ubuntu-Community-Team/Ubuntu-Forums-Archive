---
title: "Update Error Ubuntu 20.04"
date: 2020-04-20
forum: General Help
---

### Post by lord-isolator on 2020-04-20
I'm getting the following when I run 'sudo update', how do I clean this up? My software updater GUI just crashes when I try to use it.

```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:4 [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) focal InRelease       
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco InRelease                      
Get:6 [http://us.old-releases.ubuntu.com/ubuntu](http://us.old-releases.ubuntu.com/ubuntu) disco InRelease     
Err:6 [http://us.old-releases.ubuntu.com/ubuntu](http://us.old-releases.ubuntu.com/ubuntu) disco InRelease                
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Ign:7 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal InRelease                   
Get:8 [http://us.old-releases.ubuntu.com/ubuntu](http://us.old-releases.ubuntu.com/ubuntu) disco-updates InRelease
Err:8 [http://us.old-releases.ubuntu.com/ubuntu](http://us.old-releases.ubuntu.com/ubuntu) disco-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Ign:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal-backports InRelease
Ign:10 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal-security InRelease
Hit:11 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) disco-security InRelease
Ign:12 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal-updates InRelease
Err:13 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal Release
  404  Not Found [IP: 91.189.88.153 80]
Err:14 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal-backports Release
  404  Not Found [IP: 91.189.88.153 80]
Err:15 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal-security Release
  404  Not Found [IP: 91.189.88.153 80]
Err:16 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) focal-updates Release
  404  Not Found [IP: 91.189.88.153 80]
Reading package lists... Done
E: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/disco/InRelease](http://us.old-releases.ubuntu.com/ubuntu/dists/disco/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://us.old-releases.ubuntu.com/ubuntu disco InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/disco-updates/InRelease](http://us.old-releases.ubuntu.com/ubuntu/dists/disco-updates/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://us.old-releases.ubuntu.com/ubuntu disco-updates InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu focal-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu focal-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu focal-updates Release' does not have a Release file.
```
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by deadflowr on 2020-04-20
Ubuntu 20.04 focal is not an old release was no archives are available for it in the old-release repositories.
You need fix the sources.

should be able to fix it in Software and Updates, and select Download from.
toggle the selection box to Other, and in Other click on Best server.
This should choose the best mirror server for you.
When done close Software and Updates and see if it loads correctly.

---

### Post by lord-isolator on 2020-04-20
Is there away to do this from the command line? I can have it select the server, but when I go to close the updater it prompts me to reload for changes to take effect, then crashes.

---

### Post by deadflowr on 2020-04-20
Here: [https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by lord-isolator on 2020-04-20
Thank you for your help, it appears I fixed it. I replaced 
/etc/apt/sources.list

With a copy from a fresh install.

---

