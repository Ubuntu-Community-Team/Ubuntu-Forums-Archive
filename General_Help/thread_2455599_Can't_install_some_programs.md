---
title: "Can't install some programs"
date: 2020-12-23
forum: General Help
---

### Post by grxgghxrpxr on 2020-12-23
I can't open the following programs:
Shotwell, because it can't find 'libraw.so.19'
Handbrake, because it can't find 'libdvdnav.so.4'.
Do you know where I can find these?

---

### Post by TheFu on 2020-12-23
You don't need just those libraries. They have dependencies and the dependencies have dependencies.

If it was me seeking a solution, I'd look for which specific version of shotwell was released for your specific OS release and use that.  Then these dependencies will just fall into line.  If the OS is 16.04, it cannot run the 18.04 version of shotwell directly due to dependencies.  Perhaps using a PPA version for 16.04 would work, however.
Similarly, trying to use a 16.04 version of shotwell on a 20.04 OS won't work.  All the libraries that make up the OS have moved forward.

As for handbrake, I know it works on 16.04 fine with all the dependencies I've needed handled.

```
$ dpkg -l|grep handbrake
ii  handbrake-cli   1.1.2-zhb-1ppa1~xenial1    amd64  versatile DVD ripper and video transcoder - command line
ii  handbrake-gtk   1.1.2-zhb-1ppa1~xenial1    amd64  versatile DVD ripper and video transcoder - GTK GUI

```

libdvdnav.so.4 appears to be a handled dependency for handbrake to me.  It is inside the libdvdnav4 package.  
```
sudo apt install libdvdnav4
```
I don't know about other Ubuntu releases. Sorry.

It is always possible that some hardware issue is causing random problems. Check the system logs for that, unless you think some package management mistake was made by the admin of the system.

---

### Post by #&amp;thj^% on 2020-12-23
> **grxgghxrpxr said:**
> I can't open the following programs:
Shotwell, because it can't find 'libraw.so.19'
Handbrake, because it can't find 'libdvdnav.so.4'.
Do you know where I can find these?
```
locate libdvdnav.so.4
/usr/lib/x86_64-linux-gnu/libdvdnav.so.4
/usr/lib/x86_64-linux-gnu/libdvdnav.so.4.2.0

```
For Handbrake:
```
sudo add-apt-repository ppa:stebbins/handbrake-releases
$ sudo apt-get update
```
Shotwell should be in your repos:
```
apt policy shotwell
shotwell:
  Installed: 0.30.10-0ubuntu0.1
  Candidate: 0.30.10-0ubuntu0.1
  Version table:
 *** 0.30.10-0ubuntu0.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.30.8-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages

```
Shotwell dep: 
```
locate libraw.so
/usr/lib/x86_64-linux-gnu/libraw.so.19
/usr/lib/x86_64-linux-gnu/libraw.so.19.0.2

```

---

### Post by deadflowr on 2020-12-23
What have you added to the release? (in terms of any 3rdparty repositories or PPAs)

And what release of Ubuntu is it?

Shotwell is the default image managing program on Ubuntu.
While I believe it can be excluded on install if using the Installer's minimal install option,
it seems odd that it not work or open regardless of that.

---

### Post by grxgghxrpxr on 2020-12-23
> **TheFu said:**
> You don't need just those libraries. They have dependencies and the dependencies have dependencies.

If it was me seeking a solution, I'd look for which specific version of shotwell was released for your specific OS release and use that.  Then these dependencies will just fall into line.  If the OS is 16.04, it cannot run the 18.04 version of shotwell directly due to dependencies.  Perhaps using a PPA version for 16.04 would work, however.
Similarly, trying to use a 16.04 version of shotwell on a 20.04 OS won't work.  All the libraries that make up the OS have moved forward.

As for handbrake, I know it works on 16.04 fine with all the dependencies I've needed handled.

```
$ dpkg -l|grep handbrake
ii  handbrake-cli   1.1.2-zhb-1ppa1~xenial1    amd64  versatile DVD ripper and video transcoder - command line
ii  handbrake-gtk   1.1.2-zhb-1ppa1~xenial1    amd64  versatile DVD ripper and video transcoder - GTK GUI

```

libdvdnav.so.4 appears to be a handled dependency for handbrake to me.  It is inside the libdvdnav4 package.  
```
sudo apt install libdvdnav4
```
I don't know about other Ubuntu releases. Sorry.

It is always possible that some hardware issue is causing random problems. Check the system logs for that, unless you think some package management mistake was made by the admin of the system.


Thank you for this. It says it is already installed, yet it still can't find it when I try to open Handbrake. I'm using Ubuntu Budgie.

---

### Post by grxgghxrpxr on 2020-12-23
> **1fallen said:**
> ```
locate libdvdnav.so.4
/usr/lib/x86_64-linux-gnu/libdvdnav.so.4
/usr/lib/x86_64-linux-gnu/libdvdnav.so.4.2.0

```
For Handbrake:
```
sudo add-apt-repository ppa:stebbins/handbrake-releases
$ sudo apt-get update
```
Shotwell should be in your repos:
```
apt policy shotwell
shotwell:
  Installed: 0.30.10-0ubuntu0.1
  Candidate: 0.30.10-0ubuntu0.1
  Version table:
 *** 0.30.10-0ubuntu0.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.30.8-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages

```
Shotwell dep: 
```
locate libraw.so
/usr/lib/x86_64-linux-gnu/libraw.so.19
/usr/lib/x86_64-linux-gnu/libraw.so.19.0.2

```

Here is the result of me adding the repository for Handbrake (I'm using Ubuntu Budgie):

Found existing deb entry in /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-groovy.list
Adding deb entry to /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-groovy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-groovy.list
Adding key to /etc/apt/trusted.gpg.d/stebbins-ubuntu-handbrake-releases.gpg with fingerprint 43D3A9F60C58A7169778E6FB8771ADB0816950D8
Ign:1 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) groovy InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) groovy InRelease                     
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) groovy-updates InRelease [110 kB]    
Hit:4 [http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu) groovy InRelease
Hit:5 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) groovy InRelease                
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security InRelease [110 kB]     
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) groovy-backports InRelease [101 kB]  
Hit:8 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease           
Err:9 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) groovy Release
  404  Not Found [IP: 2001:67c:1560:8008::19 80]
Hit:10 [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease                     
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) groovy-updates/main amd64 DEP-11 Metadata [24.1 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) groovy-updates/universe amd64 DEP-11 Metadata [15.0 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) groovy-backports/universe amd64 DEP-11 Metadata [600 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security/main amd64 DEP-11 Metadata [4,692 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security/universe amd64 DEP-11 Metadata [2,820 B]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

I don't feel like Ubuntu Budgie wants to add this for some reason. :/

---

### Post by grxgghxrpxr on 2020-12-23
> **deadflowr said:**
> What have you added to the release? (in terms of any 3rdparty repositories or PPAs)

And what release of Ubuntu is it?

Shotwell is the default image managing program on Ubuntu.
While I believe it can be excluded on install if using the Installer's minimal install option,
it seems odd that it not work or open regardless of that.

I'm using Ubuntu Budgie 20.10.

---

### Post by TheFu on 2020-12-23
```
Hit:10 [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease 
```
is a problem. Fix that.

Never mix different release repos.  Don't.  Just don't.  Self-inflicted issues.

---

### Post by grxgghxrpxr on 2020-12-24
> **TheFu said:**
> ```
Hit:10 [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease 
```
is a problem. Fix that.

Never mix different release repos.  Don't.  Just don't.  Self-inflicted issues.

How?

---

### Post by TheFu on 2020-12-24
> **grxgghxrpxr said:**
> How?

Do the opposite of whatever you did to add it to your repo list.  It certainly wasn't there at install time and someone added it.  The way it got added matters.  
[LIST]
[*]Did you install a .deb file?  Uninstall that .deb package and hope it removes the repository.
[*]Did you run a **add-apt-repository** command?  Use an remove-apt-repository (may need to install a tool for that).
[*]Did you manually add it using an editor?  Then manually remove it.
[/LIST]

In general, installing .deb files directly is a bad idea until some level of expertise has been achieved with Ubuntu/Linux. There are often highly undesirable side-effects.  Stick with the pre-setup Canonical Repos when learning.  

Linux is very flexible and that's great in the hands of someone with a little expertise, but the Unix philosophy will let you shot yourself in the hand, foot, leg, chest and sometimes in the head.

All repositories are located somewhere under /etc/apt/ in different files there.  If you decide to manually modify any of these files, be 100% certain you make a backup and know how to put it back.  This is good advice for any system file changes for all admins.  A few months ago, I made a change and broke some parts of my system.  Because I make automatic, nightly, backups, the original version of the file was available to put back. If you don't do automatic backups, you'll want to manually do it.

---

### Post by #&amp;thj^% on 2020-12-24
> **grxgghxrpxr said:**
> Here is the result of me adding the repository for Handbrake (I'm using Ubuntu Budgie):

Found existing deb entry in /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-groovy.list
Adding deb entry to /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-groovy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-groovy.list
Adding key to /etc/apt/trusted.gpg.d/stebbins-ubuntu-handbrake-releases.gpg with fingerprint 43D3A9F60C58A7169778E6FB8771ADB0816950D8
Ign:1 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) groovy InRelease


I don't feel like Ubuntu Budgie wants to add this for some reason. :/
Just A heads up Ubuntu Budgie 20.10 is a point release, a lot of the PPA maintainers won't add to them, they want LTS versions
```
E: The repository 'http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
```
There isn't one for 20.10: [https://handbrake.fr/docs/en/latest/developer/install-dependencies-ubuntu.html](https://handbrake.fr/docs/en/latest/developer/install-dependencies-ubuntu.html)
This worked for me copying my DVD's

Try **(this is not needed for Ubuntu 20.04)**
```
sudo apt install libdvdread4
```

Do:

```
sudo apt install libdvdnav4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
    sudo dpkg-reconfigure libdvd-pkg 
    sudo apt install ubuntu-restricted-extras
```
Handbrake:
```
apt policy handbrake
handbrake:
  Installed: 1.3.1+ds1-1build1
  Candidate: 1.3.1+ds1-1build1
  Version table:
 *** 1.3.1+ds1-1build1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status

```

After that I was able to copy "My" DVD's.
Note libdvdread4 is unavailable in Ubuntu 20.04, but seems unneeded.
If it were me I'd just remove the "**[https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease**".

Follow this for windscribe: [https://windscribe.com/guides/manual_ubuntu](https://windscribe.com/guides/manual_ubuntu)

---

### Post by Dennis N on 2020-12-24
> I don't feel like Ubuntu Budgie wants to add this for some reason.

If you know the basics of Flatpak installation, another option would be to install the Flatpak version (which is 1.3.3). No PPAs involved.

```
[dmn@Tyana ~]$ flatpak search handbrake
Name                           Description                       Application ID                      Version Branch Remotes
HandBrake                      Video Transcoder                  fr.handbrake.ghb                    1.3.3   stable flathub

```

---

