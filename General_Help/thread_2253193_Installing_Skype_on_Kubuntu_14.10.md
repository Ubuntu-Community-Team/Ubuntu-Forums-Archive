---
title: "Installing Skype on Kubuntu 14.10"
date: 2014-11-17
forum: General Help
---

### Post by pwabrahams on 2014-11-17
I'm trying to install Skype on Kubuntu 14.10.  I've found lots of posts on this subject, but the suggestions don't work for me.  Furthermore, trying them has hosed my system twice.

The first question is what program to use to install deb packages.  Most of the posts recommend **gdebi**, but my attempts to install **gdebi** have all been unsuccessful, with these messages:```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gdebi : Depends: gir1.2-gtk-3.0 but it is not going to be installed
         Depends: gir1.2-vte-2.90 but it is not going to be installed
         Recommends: libgtk2-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I've tried all the following to get past that:
  ```
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get clean

```
None of these make the slightest difference.

The packages I'm trying to install, which come from the Skype website, are:
```
skype-debian_4.3.0.37-1_i386.deb
skype-ubuntu-precise_4.3.0.37-1_i386.deb

```
I've also tried to install them with QApt Package Installer, but that leads to a disaster if I follow through on it: the installer attempts to install 1776 other packages and in the process removes a whole bunch of ones I'm using.such as **systemsettings**.

So how can I do this installation?  And does qdebi even work on 14.10?

---

### Post by ian-weisser on 2014-11-18
I would trash the packages you downloaded from the Skype website.
Instead, I would use the version of Skype already in the Partner Repositories. 
See [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) . Three commands, and it's installed.

You cannot install gdebi - you have something else installed already that conflicts with gdebi
The only way you can install gdebi using the package manager is to identify that  'something else' and uninstall it.

---

### Post by pwabrahams on 2014-11-18
I've tried those steps, with no success.  I have this in my /etc/apt/sources.list:

```
deb http://archive.canonical.com/ utopic partner
deb-src http://archive.canonical.com/ utopic partner
```

as well as this, produced by the Ubuntu Sources Generator:

```
###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu trusty partner

```

I also did this:

```
sudo dpkg --add-architecture i386
```

and this:
```
sudo apt-get update
```

But here's what I get:```
root@morchella:~# apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
root@morchella:~# apt-get remove skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'skype' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

---

### Post by ian-weisser on 2014-11-18
The problem is not Skype, nor your method of install.

You have installed conflicting software sometime in the past, and that conflict has broken your package manager.
You won't be able to install anything until you locate and uninstall the conflicting software.
Er, you may not be receiving security updates. They use the same package manager.

Do you recall what you might have installed before the package manager broke?
The usual cause is software from a PPA or some other non-Ubuntu source.

---

### Post by pwabrahams on 2014-11-20
I finally gave up on trying to install Skype relatively late in the process of setting up my system.  I did a reinstall from scratch (reformatted partition) and installed Skype as the first post-install action according to the well-known "good" instructions and have had no difficulty since.

Unfortunately, (K)ubuntu is ineffective at locating the source of package conflicts.  The question is simple: what packages need to be removed in order to avoid the reported conflicts.  I suppose that's worth asking in a separate post.

---

### Post by ian-weisser on 2014-11-20
apt and dpkg, which are standard across all distributions of Ubuntu, handles package management. All package managers are mere frontends for these utilities.

The key to tracking down conflicts is to dig down the chain of dependencies.
So, if Skype won't install due to a conflict in skype-bin,
next you try to install skype-bin (instead of skype) to see those error messages.
After one or two or three links in this causal chain, you come up with the specific problem (Example: two packages trying to provide the same file)

---

