---
title: "trying to fix a camera problem and got mystery"
date: 2019-02-28
forum: General Help
---

### Post by jgw on 2019-02-28
I was trying to fix, and view my logitech webcam pro 9000.  It worked in cheese but only sometimes and only on the lowest resolution which gave a lousy picture.  I checked my camera's specs and noted that it produced resolutions conserably better than cheese seemed capable of.   Anyway, I then searched and found I should have guvcview.  I went to ickmcjohnnson.blogspot.com/2011/07/logitech-webcam-pro-9000-running-under.html and did as instructed.  I already had guvcview installed but figured this would update it just to make sure it was the latest and greatest.  During the upgrade I had errors:
E: /var/cache/apt/archives/libguvcview-2.0-0_2.0.6+ubuntu2~ppa1+1429-0ubuntu1~201810062214~ubuntu18.04.1_amd64.deb: trying to overwrite '/usr/lib/x86_64-linux-gnu/libgviewaudio-2.0.so.2.0.0', which is also in package libguvcview-2.0-2:amd64 2.0.5+debian-1

The  I ran guvcview and I got:
could not start a video stream in the device
You seem to have video devices installed
Do you want try one?
the  device:  UVC Camera (046d:0809)

then I ran cheese and was told: there was an error playing from the webcam

then synaptic told me I had a problem and to: sudo apt-get install -f which gave me:sudo apt-get install -f
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  caribou gnome-calculator gnome-characters gnome-logs gnome-online-miners
  gnome-system-monitor libgfbgraph-0.2-0 libguvcview-2.0-2 libzapojit-0.0-0
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libguvcview-2.0-0
The following NEW packages will be installed:
  libguvcview-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/120 kB of archives.
After this operation, 339 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 226217 files and directories currently installed.)
Preparing to unpack .../libguvcview-2.0-0_2.0.6+ubuntu2~ppa1+1429-0ubuntu1~201810062214~ubuntu18.04.1_amd64.deb ...
Unpacking libguvcview-2.0-0:amd64 (2.0.6+ubuntu2~ppa1+1429-0ubuntu1~201810062214~ubuntu18.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libguvcview-2.0-0_2.0.6+ubuntu2~ppa1+1429-0ubuntu1~201810062214~ubuntu18.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libgviewaudio-2.0.so.2.0.0', which is also in package libguvcview-2.0-2:amd64 2.0.5+debian-1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libguvcview-2.0-0_2.0.6+ubuntu2~ppa1+1429-0ubuntu1~201810062214~ubuntu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

seems I have cleverly created a mess.

Any thoughts would really be appreciated.

---

### Post by HermanAB on 2019-03-01
You could use gstreamer or ffmpeg directly, not through cheese.

[http://wiki.oz9aec.net/index.php/Gstreamer_Cheat_Sheet](http://wiki.oz9aec.net/index.php/Gstreamer_Cheat_Sheet)
[https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html](https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html)
[https://www.aeronetworks.ca/2017/08/digital-slow-scan-tv-with-gstreamer.html](https://www.aeronetworks.ca/2017/08/digital-slow-scan-tv-with-gstreamer.html)

---

### Post by jgw on 2019-03-02
thanks for the reply!

I installed guvcview and it fixed the problem

---

