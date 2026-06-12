---
title: "Install cdemu on Precise Pangolin 12.04"
date: 2014-11-22
forum: General Help
---

### Post by Ralph L on 2014-11-22
I am trying to install cdemu on Ubuntu Precise Pangolin 12.04.  I went to [https://launchpad.net/~garhuy/+archive/ubuntu/precise?field.series_filter=precise](https://launchpad.net/~garhuy/+archive/ubuntu/precise?field.series_filter=precise) and installed the ppa:garhuy/precise ppa using:```
sudo add-apt-repository ppa:garhuy/precise
sudo apt-get update
```  and then tried to install cdemu from the garhuy ppa ```
sudo apt-get install cdemu-daemon cdemu-client
```  I then get the message "Media change: please insert the disc labeled
 'Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)'
in the drive '/media/cdrom/' and press enter"

I don't have a 12.04.2 disk and can't find a download for it.  All downloads are for 12.04.4 or 12.04.5.

I would appreciate any help.

---

### Post by deadflowr on 2014-11-22
You can get 12.04, 12.04.1, 12.04.2 here
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

You have to scroll down until you find the desktop iso for the version you want.
If you need 12.04.2 desktop 32-bit(i386) version look for the one
ubuntu-12.04.2-desktop-i386.iso
Here's the release date to help a little further
 [COLOR=#000000]13-Feb-2013 22:22  693M  Desktop CD for PC (Intel x86) computers (standard download)[/COLOR]

---

### Post by Ralph L on 2014-11-22
deadflowr
Thank you very much for responding.  I found the 12.04.2 release, downloaded it, and burned a cd.  However, the command:"sudo apt-get install cdemu-daemon cdemu-client" would not accept the disk and kept asking for 'Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)'.  The disk came up in Nautilus as "Ubuntu 12.04.2 LTS i386" so the name is different even though it is the correct Ubuntu release, so I still have a problem.

I really don't understand why the installation process needs a disk.  No other installations I have done required that.  Could explain why the disk is needed.  Also, I don't know how to rename the disk so that the installation will accept it.  

I didn't explain why I was installing cdemu.  It is so I can run a game that came on a cd that requires the cd to always be present in the cd drive.  I want cdemu so that I can emulate a cd on my hard drive and not need to insert the cd every time I run the game.  If there is a better way to accomplish this than using cdemu, please so advise.

Thank you in advance.

---

### Post by Ralph L on 2014-11-22
I made progress.  I brought up Synaptic and found that under Settings>Repositories>Ubuntu Software>Installable from CD-ROM/DVD, I had "Cdrom with Ubuntu 12.04 'Precise Pangolin'" and the checkbox had a check in it.  I unchecked the checkbox and now```
sudo add-apt-repository ppa:cdemu/ppa
sudo apt-get update && sudo apt-get install gcdemu cdemu-client
``` ran to completion.  
cdemu installed ok, but I guess I don't understand it.  When I tried to load my game cd into it, it kept asking for a single file.  Apparently it wants an iso file, which my game cd is not.  Any ideas on how I can get my game cd onto my hard disk as a "virtual cd"?

Thanks

---

### Post by Ralph L on 2014-11-23
See [http://ubuntuforums.org/showthread.php?t=2253834](http://ubuntuforums.org/showthread.php?t=2253834) (a new thread I started on how to make a virtual drive from a cd) for answers to questions I posted here.

---

