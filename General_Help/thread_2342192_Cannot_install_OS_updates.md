---
title: "Cannot install OS updates"
date: 2016-11-04
forum: General Help
---

### Post by David4321 on 2016-11-04
This has been going on for months now. Updates will not complete. In software center I can install individual updates to software listed, but large package of OS updates seems to start, but progress bar stalls at about 1/8 in, and never goes further. How to resolve?

---

### Post by QIII on 2016-11-04
Hello!

We'll need some information.

Could you please run 

```
sudo apt update
```

(use apt-get if your release is older than 16.04)

in the terminal and paste the results back here inside code tags?

---

### Post by bearlake on 2016-11-04
Hi,

You should at least post what version of Ubuntu and flavor you are using.

Add your source.list and sources.list.d would help a lot as well.

Post your full output and errors from:

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

beat by the big guy... :(

---

### Post by QIII on 2016-11-04
The results of update will tell us the release...

Two birds, one stone or something like that.  :)

---

### Post by RobGoss on 2016-11-04
What happens when you update from the command line do you get any errors?

```
 sudo apt-get update
```

If in fact you do get any errors post them back here using the code tags

---

### Post by David4321 on 2016-11-04
I'm running Ubunto 16.04 LTS

There are no errors when I try to update from the software center, it just hangs and never completes until I kill the process. I've let it run for hours. 

Here's sudo apt update results:

```
david@Aurora:~$ sudo apt update
[sudo] password for david: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:5 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Get:6 [http://APT.spideroak.com/ubuntu-spideroak-hardy](http://APT.spideroak.com/ubuntu-spideroak-hardy) release InRelease [2,539 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]   
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Hit:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Err:6 [http://APT.spideroak.com/ubuntu-spideroak-hardy](http://APT.spideroak.com/ubuntu-spideroak-hardy) release InRelease        
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 573E3D1C51AE1B3D
Hit:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Hit:10 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb InRelease                   
Ign:12 [http://ppa.launchpad.net/asukhovatkin/unity-launcher-folders/ubuntu](http://ppa.launchpad.net/asukhovatkin/unity-launcher-folders/ubuntu) xenial InRelease
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [417 kB]
Hit:14 [http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu](http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu) xenial InRelease  
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [412 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [161 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 Packages [6,576 B]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages [6,528 B]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en [2,016 B]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [357 kB]
Hit:21 [http://ppa.launchpad.net/obsproject/obs-studio/ubuntu](http://ppa.launchpad.net/obsproject/obs-studio/ubuntu) xenial InRelease  
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [354 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages [7,048 B]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [5,856 B]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Translation-en [2,868 B]
Err:26 [http://ppa.launchpad.net/asukhovatkin/unity-launcher-folders/ubuntu](http://ppa.launchpad.net/asukhovatkin/unity-launcher-folders/ubuntu) xenial Release
  404  Not Found
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [157 kB]
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [81.5 kB]
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [62.9 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages [6,576 B]
Get:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [6,528 B]
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [200 B]
Reading package lists... Done                                    
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: GPG error: [http://APT.spideroak.com/ubuntu-spideroak-hardy](http://APT.spideroak.com/ubuntu-spideroak-hardy) release InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 573E3D1C51AE1B3D
E: The repository 'http://APT.spideroak.com/ubuntu-spideroak-hardy release InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/asukhovatkin/unity-launcher-folders/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
david@Aurora:
```

---

### Post by QIII on 2016-11-04
Hello!

For now, just to get everything else updated, disable that spideroak repo and the launchpad PPA in your sources list.

Then you can work on what the issue is with them.  (I'd just avoid anything packaged for Hardy).

---

### Post by David4321 on 2016-11-04
Great, thank you. I don't know how to disable those two, instructions please.


I have the results of sudo apt-get upgrade if you want to see, but it won't let me post or attach, it's 138kb.

Ok, here you go: [http://passionateawakenings.com/files/upgrade.txt](http://passionateawakenings.com/files/upgrade.txt)

---

### Post by RobGoss on 2016-11-05
Hello and welcome, You can access your source list by opening up **Software & updates,** click on **Other** **Software, **you will see a list of installed **PPA's **you can disable them by unchecking the itemsthat **Qlll **recommended to disable

---

### Post by David4321 on 2016-11-05
It's ok, updates succeeded after the terminal update and upgrade commands. Thank you!

---

### Post by RobGoss on 2016-11-05
That's great if your issue is solved you can mark this thread as solved by using the **Thread Tool **at the top of this post.

Thanks so much

---

