---
title: "Trying to re-install gimp"
date: 2021-02-15
forum: General Help
---

### Post by jgw on 2021-02-15
I had some problems trying to clean up my desktop.  Below is what happened when I tried to update.

```

greg@gregdown:~$ sudo apt update
[sudo] password for greg: 
Ign:1 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal InRelease
Err:2 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu focal InRelease                      
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [109 kB]      
Get:6 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:7 http://ppa.launchpad.net/jcfp/nobetas/ubuntu focal InRelease             
Hit:8 http://archive.canonical.com/ubuntu focal InRelease                      
Get:9 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]   
Hit:10 http://ppa.launchpad.net/jcfp/sab-addons/ubuntu focal InRelease
Hit:11 http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease
Hit:12 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal InRelease
Hit:13 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu focal InRelease
Hit:14 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu focal InRelease
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

greg@gregdown:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
greg@gregdown:~$ 

```

I then went to synaptic and tried to reinstall gimp (it failed) then I told it to fix broken packages and got:
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

then I asked synaptic for a held packages and got:
```

icad-templates                   5.1.5-1                     project templates for kicad
libsane				1.0.29-0ubuntu5       API library for scanners
matchbox                          1:6                           base X environment for resource-limited system
r-cran-polycub                   0.7.1-1                     GNU R Cubature over Polygonal Domains
zietgeist                            1.0.2.3ubuntu2         event logging framwork

```

After that I stopped.  I did try some other stuff but I am stuck with mysterious things such as held packages.  Until I fix this I can do nothing.  I was thinking of downloading and re-installing gimp but figure that would just complicate stuff.  I am also considering downloading ubuntu 20.10 and installing that just to see if that fixes anything but decided to write this instead.  Any help would be appreciated.

Thoughts?

---

### Post by CelticWarrior on 2021-02-15
Nothing happened with the apt update / apt upgrade process except the error about the 'cdrom' also explained [here]("https://ubuntuforums.org/showthread.php?t=2457843").
Why where you trying to reinstall Gimp? What's the result of ```
sudo apt install --reinstall gimp
```

---

### Post by rsteinmetz70112 on 2021-02-15
I notice you appear to have have 
```
Ign:1 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal InRelease
Err:2 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release
```
Do you have that in your sources? If you don't need it you might want to remove it.

Have you tried to explicitly update the held packages of reinstall them?

```
apt install icad-templates --reinstall
```

---

### Post by UltimateCat on 2021-02-16
APT is looking for the cdrom. In other words it's looking for the cd that you install Ubuntu with.

You should edit your sources list and uncomment the cdrom argument.

---

