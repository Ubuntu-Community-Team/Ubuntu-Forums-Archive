---
title: "Update Manger Not working"
date: 2013-02-02
forum: General Help
---

### Post by Singularity64 on 2013-02-02
Hi
I am running Uubuntu 10.04 and was trying to fix a problem with matplotlib package,and in the process, I added sources to my repository corresponding to version 12.04. When I upgraded, I was left with several broken packages which I tried to correct using apt-get variations and dpkg commands with little luck. 

At this point, my update manager is not working. Here is the output from the terminal.

```
$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
```


I have looked up dozens of forum posts but no luck. Here is what I get when I try to install pygtk:

```
sudo aptitude install pygtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find package "pygtk".  However, the following
packages contain "pygtk" in their name:
  python-zbarpygtk 
Couldn't find package "pygtk".  However, the following
packages contain "pygtk" in their name:
  python-zbarpygtk 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

I am really consideration a reinstallation. If that's the option, could you please recommend the best way to save my settings so that I can restore that after reinstalling Ubuntu. Thank You.

---

### Post by raja.genupula on 2013-02-02
try with

```
sudo apt-get install --reinstall update-manager
```

---

### Post by Singularity64 on 2013-02-02
> **raja.genupula said:**
> try with

```
sudo apt-get install --reinstall update-manager
```

No luck, this was the output:
```
sudo apt-get install --reinstall update-manager
[sudo] password for kvrn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/801kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 199709 files and directories currently installed.)
Preparing to replace update-manager 1:0.134.12.1 (using .../update-manager_1%3a0.134.12.1_all.deb) ...
Unpacking replacement update-manager ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
ERROR: Cannot import gmenu, is a package upgrade in progress?
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up update-manager (1:0.134.12.1) ...

Processing triggers for python-central ...
```

Then trying to run update-manager gives the same error about no mudule named pygtk.

---

### Post by stinkeye on 2013-02-02
You could try purging the ppa's you added to get back to your original state.
The added ppas must still be enabled to purge.

---

### Post by raja.genupula on 2013-02-03
> **stinkeye said:**
> You could try purging the ppa's you added to get back to your original state.
The added ppas must still be enabled to purge.

+1 . you can also do like from software sources , uncheck that PPA and re-update your cache with sudo apt-get update.

---

### Post by Singularity64 on 2013-02-07
> **raja.genupula said:**
> +1 . you can also do like from software sources , uncheck that PPA and re-update your cache with sudo apt-get update.

I finally burned a Ubuntu 12.04 Live CD and used that to carry out the upgrade. Most of it went through smoothly and while there are packages that I needed to reinstall, I was able to get Basemap and everything else that I required working properly.  

What I learned from this experience is that if your system has reach a point where nothing appears to work, then you are likely to save far more time doing an upgrade/reinstallation through Live CD. 

Of course, this cannot be some universal rule: there can always be situations where the risk is very high.

Thanks to everyone for their advice!

---

