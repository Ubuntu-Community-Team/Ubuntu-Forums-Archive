---
title: "How to install uctimsclient on ubuntu 10.04"
date: 2013-07-02
forum: General Help
---

### Post by isaroma on 2013-07-02
Hi All, 
I installed Open IMS Core in Ubuntu 10.04, 
the next step, I want to install uctimsclient in Ubuntu 10.04 as client of OpenIMSCore that was I installed, 

I downloaded [uctimsclient1.0.13.deb]("http://prdownload.berlios.de/uctimsclient/uctimsclient1.0.13.deb") at [https://developer.berlios.de/project/showfiles.php?group_id=7844](https://developer.berlios.de/project/showfiles.php?group_id=7844)
but after I execute dpkg -i [uctimsclient1.0.13.deb]("http://prdownload.berlios.de/uctimsclient/uctimsclient1.0.13.deb")
it tells that UCT IMS needs some dependencies, and I should install the dependency packages
and here that packages :

[LIST]
[*]apt-get install libosip2-3deb
[*]apt-get install libexosip2-dev
[*]apt-get install libgtk2.0-dev
[*]apt-get install libxml2-dev
[*]apt-get install libcurl4-openssl-dev
[*]apt-get install libgstreamer0.10-0
[*]apt-get install libgstreamer-plugins-base0.10-dev
[*]apt-get install gstreamer0.10-plugins-base
[*]apt-get install gstreamer0.10-plugins-good
[*]apt-get install gstreamer0.10-plugins-bad
[*]apt-get install gstreamer0.10-plugins-ugly
[*]apt-get install gstreamer0.10-ffmpeg
[*]apt-get install libavcodec-unstripped-51
[*]apt-get install libvlc-dev
[*]apt-get install vlc
[/LIST]

all of them can be installed, except libosip2-3deb and libavcodec-unstripped-51

how can i resolve this problem?  Did the steps that I did was wrong ? 
Should I change repository to install the dependencies?

Please Help me, thanks

---

### Post by dino99 on 2013-07-02
pay attention at the 10.04 end-of-life : only the server is still alive  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
take note also that ubuntu do some tweaks with the packages configuration/dependency, so use the ubuntu packages first if they exist  [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

you can force dpkg (at your own risk indeed): sudo dpkg --force-depends -i filename.deb to install and sudo dpkg --force-depends -r packagename to remove.

[http://uctimsclient.berlios.de/openimscore_on_ubuntu_howto.html](http://uctimsclient.berlios.de/openimscore_on_ubuntu_howto.html)

---

