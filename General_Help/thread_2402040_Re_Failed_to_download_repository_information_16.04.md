---
title: "Re: Failed to download repository information: 16.04"
date: 2018-09-25
forum: General Help
---

### Post by lymphor on 2018-09-25
I'm getting the same message: ***Failed to download repository information***.
Went to terminal and typed **sudo apt update**, this is the output:

```
Err:1 [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb InRelease
  Could not resolve 'archive.getdeb.net'
Hit:2 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial InRelease
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:4 [http://ppa.launchpad.net/jonathonf/ffmpeg-3/ubuntu](http://ppa.launchpad.net/jonathonf/ffmpeg-3/ubuntu) xenial InRelease      
Hit:5 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease        
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:7 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial InRelease 
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release               
Hit:9 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                      
Hit:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease            
Hit:11 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu) xenial InRelease
Hit:12 [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) xenial InRelease  
Hit:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security InRelease           
Hit:14 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial InRelease
Hit:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease    
Hit:16 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease)  Could not resolve 'archive.getdeb.net'
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
ale@alePC:~$ sudo apt update
Err:1 [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb InRelease
  Could not resolve 'archive.getdeb.net'
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                     
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                                                       
Hit:4 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease                                                                          
Hit:5 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial InRelease                                                         
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                                                                       
Hit:7 [http://ppa.launchpad.net/jonathonf/ffmpeg-3/ubuntu](http://ppa.launchpad.net/jonathonf/ffmpeg-3/ubuntu) xenial InRelease                                                 
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                
Hit:9 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                                                 
Hit:10 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial InRelease                     
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Hit:12 [http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu](http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu) xenial InRelease                          
Hit:13 [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) xenial InRelease                                   
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]                                   
Hit:16 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial InRelease       
Hit:17 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease                       
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]                       
Fetched 323 kB in 1s (215 kB/s)                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list:2 and /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list:3
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease)  Could not resolve 'archive.getdeb.net'
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages (apps/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Packages (apps/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Translations (apps/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11 (apps/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target DEP-11-icons (apps/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/getdeb.list:1 and /etc/apt/sources.list.d/getdeb.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list:2 and /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list:3
```

Could anybody please help me?
 Thank you in advance! :)

---

### Post by lymphor on 2018-09-25
_*LATER EDIT*:_ when prompted the mentioned message I entered **Settings > Other Software** and unticked all the items except **Canonical Partners** and then repeated the update procedure. Issue fixed.
 Apparently there was one item causing the problem, more precisely **[http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/xenial-getdeb/InRelease)**.
You can identify the item causing your issue by ticking them back one by one and trying to update. Hope this helps! ;-)

---

### Post by deadflowr on 2018-09-25
Post moved to it's own thread
(previous thread here:[https://ubuntuforums.org/showthread.php?t=2399515]("https://ubuntuforums.org/showthread.php?t=2399515")


Per the issue, you need to remove the getdeb repo from your source entries as it is dead.
Easiest way to do that is using The Software and Updates app , toggle over to the Other Software section and go down to the getdeb entry(ies) and uncheck them.
The exit and let it reload .

ninja'd

On a related note, discussion here:[https://ubuntuforums.org/showthread.php?t=2401312]("https://ubuntuforums.org/showthread.php?t=2401312")
On the state of getdeb.

---

