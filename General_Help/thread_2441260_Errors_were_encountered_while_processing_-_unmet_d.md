---
title: "Errors were encountered while processing - unmet dependencies"
date: 2020-04-21
forum: General Help
---

### Post by gerrit20 on 2020-04-21
Hi! I am trying to install ROS in Ubuntu. I used this link: [http://wiki.ros.org/Installation/Ubuntu](http://wiki.ros.org/Installation/Ubuntu). But I get an error everytime, 'unmet dependencies', copy pasted below. Does anyone know what I can do to fix this?? Thank you in advance :)


The things I already tried are:
- sudo apt update
- sudo apt full-upgrade
- sudo apt-get upgrade dpkg
- sudo dpkg -r --force-all python-rospkg
- sudo apt --fix-broken install
- sudo apt-get remove ros-*
- sudo apt-get install python-rosdep
- sudo apt-get remove python-rosdep
- sudo apt-get remove python-rosinstall
- sudo apt-get remove python-rosinstall-generator
- sudo apt-get remove python-wstool
- sudo apt install ros-melodic-desktop-full
- sudo apt-get remove python-rosdep-modules
- sudo apt list --upgradable
- sudo apt-get purge python-ros*


```
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python-rosdep-modules : Depends: python-rospkg-modules (>= 1.1.10) but it is not installed
                         Depends: python-rosdistro-modules (>= 0.7.5) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by slickymaster on 2020-04-21
*Thread moved to **General Help**.*

---

### Post by ActionParsnip on 2020-04-21
If you run:

sudo apt-get -f install

What is the output please? Also please give the output of:

lsb_release -a; uname -a

Thanks

---

### Post by gerrit20 on 2020-04-22
Thanks for your reaction!!

The output of sudo apt-get -f install is:

```
sudo apt-get -f install
[sudo] password for mechteld: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  python-rosdistro-modules
The following NEW packages will be installed:
  python-rosdistro-modules
0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
447 not fully installed or removed.
Need to get 0 B/31,4 kB of archives.
After this operation, 263 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 213846 files and directories currently installed.)
Preparing to unpack .../python-rosdistro-modules_0.8.1-1_all.deb ...
Unpacking python-rosdistro-modules (0.8.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/python-rosdistro-modules_0.8.1-1_all.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/rosdistro/__init__.py', which is also in package python-rosdistro 0.6.6-1
Errors were encountered while processing:
 /var/cache/apt/archives/python-rosdistro-modules_0.8.1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Output of lsb_release -a; uname -a:

```
lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic
Linux mechteld-HP-ZBook-Studio-G5 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by slickymaster on 2020-04-22
@gerrit20:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting terminal output because when posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by ActionParsnip on 2020-04-22
What is the output of:

```

apt-cache policy package python-rosdistro python-rosdistro-modules

```

I can smell a PPA. Your packages have a file overlap and dpkg doesn't like that (As you can see from the error)

---

### Post by Impavidus on 2020-04-22
There's a conflict between the packages python-rosdistro-modules (which is from your PPA) and python-rosdistro (which is from the official repositories). Such conflicts are not uncommon when working with PPAs. Maybe the PPA has a new version of python-rosdistro that avoids the conflict. Probably best to remove all ROS-related packages before installing from the PPA.

Your package manager says:```
0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
447 not fully installed or removed.

```104 upgrades waiting is quite a lot and may make it a bit harder to install stuff. Installing new packages from the repos may necessitate installing some of those upgrades. I always install all upgrades immediately.

However, 447 packages partially installed is insane. It must be one of the highest numbers I've ever seen. Did that all happen at once, when you tried to install ROS? Or is this a problem that has been going on for longer? In that case it may take hours to untangle the mess. In other words, not worth the effort.

---

### Post by gerrit20 on 2020-04-22
The output of 

```

apt-cache policy package python-rosdistro python-rosdistro-modules

```


```

python-rosdistro:
  Installed: 0.6.6-1
  Candidate: 0.8.1-100
  Version table:
     0.8.1-100 500
        500 http://packages.ros.org/ros/ubuntu bionic/main amd64 Packages
        500 http://packages.ros.org/ros/ubuntu bionic/main i386 Packages
 *** 0.6.6-1 500
        500 http://nl.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://nl.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status
python-rosdistro-modules:
  Installed: (none)
  Candidate: 0.8.1-1
  Version table:
     0.8.1-1 500
        500 http://packages.ros.org/ros/ubuntu bionic/main amd64 Packages
        500 http://packages.ros.org/ros/ubuntu bionic/main i386 Packages
N: Unable to locate package package

```

I hope you can help me further with this! THanks :)

---

### Post by gerrit20 on 2020-04-22
I think something went wrong with installing then. I just installed Ubuntu on my laptop so I can use ROS. The error happened when I was first trying to install ROS. After this, I tried a few possible solutions I found on other forums, like I mentioned above. These solutions did not help but maybe this is the reason there are a lot of upgrades/packages.

I tried several times to install ROS after I got the error. I don't know if this could be the reason there are a lot of uninstalled packages/upgrades. 

You said it may take hours to untangle the mess, but is there a way to uninstall all of it and install it again?

Thanks for your help :)

---

### Post by CelticWarrior on 2020-04-22
The OS should be fully updated before the installation of additional software, especially those from third-party sources (PPAs).

---

### Post by gerrit20 on 2020-04-22
I tried updating the OS but when I do so, I get the following output.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
151 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python-rosdep-modules : Depends: python-rosdistro-modules (>= 0.7.5) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

As you said, you have to fully update before the installation of additional software. When I first tried to install ROS, I did run an update of the OS. Afterwards, I still got the errors. So I am not sure what to do next to fix this problem.

---

