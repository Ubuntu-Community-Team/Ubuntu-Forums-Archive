---
title: "Problem with Software Update v16.04 LTS"
date: 2017-10-04
forum: General Help
---

### Post by Rick St. George on 2017-10-04
After seeing the Orange Triangle appear in Panel, I clicked "View Upgrades" - there were no upgrades!

Brought up Synaptic Pkg. Mgr. and looked at "upgradeable". There were many, and one is Libgtk2.0 but it will remove the following;
(audacious, greybird theme, openshot, ubuntusudio-desktop, ubuntustudio-desktop-core)
none of which I want to remove.

What is going on with "Software Updater" and upgradeable pkgs that want to remove other software? 
If a pkg is upgradeable, how can I prevent it from removing software I want to keep?

Thanks for any input.

Rick
:popcorn:

---

### Post by ajgreeny on 2017-10-04
*Thread moved to **General Help**.* which is more appropriate and a better fit as this is not related to installation or OS version upgrade.

---

### Post by Rick St. George on 2017-10-16
Thanks for moving the Thread. Another example: I'm looking at Synaptic Pkg Mgr / Missing Recommends and see "libgpod-common" and "libgpod4-nogtk" and thought I might need these since GTKPOD doesn't seem to be working right. However, upon checking on "libgpod4-nogtk" it shows it will remove the following;
GTKPOD; LIBATOMICPARSLEY; LIBGPOD4; LIBGTKPOD1; RHYTHMBOX-PLUGINS.

So, not only will it Remove itself, it will remove the very program it is supposed to support!  Any logic in this at all?
Anyone care to guess or steer me in the right direction? 

thanks!
:popcorn:

---

### Post by again? on 2017-10-16
Are you using any third party repositories?
Command to show enabled sources:
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```
May also want to post the output from:
```
sudo apt update
```

---

### Post by Rick St. George on 2017-10-17
Output Sources.List:

```

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu/ xenial main restricted

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
# deb-src http://deb.opera.com/opera-stable/ stable non-free

```

Output Update:

```

Hit:1 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease           
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]      
Hit:5 http://deb.opera.com/opera-stable stable InRelease                       
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Get:7 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [60.3 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main Sources [278 kB]    
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [642 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [609 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [213 kB]
Fetched 2,374 kB in 5s (427 kB/s)                                     
Reading package lists... Done

```

See also this post on my output of "Autoremove" anomalies.
[https://ubuntuforums.org/showthread.php?t=2374499](https://ubuntuforums.org/showthread.php?t=2374499)

Any suggestions? Thanks!

---

### Post by again? on 2017-10-17
...and output from 
```
sudo apt upgrade
```

---

### Post by Rick St. George on 2017-10-17
You can see posted link above for yesterday's "upgrade", but ran it again now! Here is output as DKMS was apparently upgraded;

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin linux-headers-lowlatency
  linux-image-lowlatency linux-lowlatency
The following packages will be upgraded:
  dkms
1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 66.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.5 [66.3 kB]
Fetched 66.3 kB in 0s (82.5 kB/s)
(Reading database ... 346477 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.5_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.5) over (2.2.0.3-2ubuntu11.3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11.5) ...
Installing new version of config file /etc/kernel/prerm.d/dkms ...

```

---

### Post by Rick St. George on 2017-10-17
What I did here;

must have fixed it, as I no longer see anything under "upgradeable". Also 'deadflowr' posted this -

> 
Active only as it relates to that kernel. Not active as in "in use".
It's clearing the old 4.4.0-83 kernel so it needs to remove the built modules for it.
Simple as that.


Which helped to understand the difference. Will consider case closed.
Thanks Everyone!
):P

---

