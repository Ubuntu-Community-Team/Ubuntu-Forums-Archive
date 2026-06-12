---
title: "Firejail vs Xubuntu Desktop"
date: 2019-09-12
forum: General Help
---

### Post by uRock on 2019-09-12
Hiya!

I just went to install Firejail and it triggers apt to show packages as being removable. Why would it need to remove xubuntu-desktop?
```
~$ sudo apt install firejail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool libxatracker2 linux-generic-hwe-18.04 linux-image-generic-hwe-18.04 thermald x11-apps x11-session-utils xinit xserver-xorg-legacy-hwe-18.04 xserver-xorg-video-all-hwe-18.04 xserver-xorg-video-amdgpu-hwe-18.04
  xserver-xorg-video-ati-hwe-18.04 xserver-xorg-video-fbdev-hwe-18.04 xserver-xorg-video-intel-hwe-18.04 xserver-xorg-video-nouveau-hwe-18.04 xserver-xorg-video-qxl-hwe-18.04 xserver-xorg-video-radeon-hwe-18.04 xserver-xorg-video-vesa-hwe-18.04
  xserver-xorg-video-vmware-hwe-18.04
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  firejail-profiles ssh-askpass
Recommended packages:
  xpra | xserver-xephyr | xvfb
The following packages will be REMOVED:
  xorg xserver-xorg-hwe-18.04 xubuntu-core xubuntu-desktop
The following NEW packages will be installed:
  firejail firejail-profiles ssh-askpass
0 upgraded, 3 newly installed, 4 to remove and 0 not upgraded.
Need to get 313 kB of archives.
After this operation, 1,143 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
Those autoremovable packages don't show up when I go to install something else, like Wireshark.
```
sudo apt install wireshark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libc-ares2 libmaxminddb0 libnl-route-3-200 libqgsttools-p1 libqt5multimedia5
  libqt5multimedia5-plugins libqt5multimediawidgets5 libqt5opengl5 libsmi2ldbl libwireshark-data
  libwireshark11 libwiretap8 libwscodecs2 libwsutil9 wireshark-common wireshark-qt
Suggested packages:
  mmdb-bin snmp-mibs-downloader wireshark-doc
The following NEW packages will be installed:
  libc-ares2 libmaxminddb0 libnl-route-3-200 libqgsttools-p1 libqt5multimedia5
  libqt5multimedia5-plugins libqt5multimediawidgets5 libqt5opengl5 libsmi2ldbl libwireshark-data
  libwireshark11 libwiretap8 libwscodecs2 libwsutil9 wireshark wireshark-common wireshark-qt
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.1 MB of archives.
After this operation, 106 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
Thanx to any and all who respond.

---

### Post by TheFu on 2019-09-12
What happens with the --no-install-recommends option?

---

### Post by uRock on 2019-09-12
> **TheFu said:**
> What happens with the --no-install-recommends option?

It installed. I will reboot and see if I broke anything.
```
sudo apt install firejail --no-install-recommends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  firejail-profiles xpra | xserver-xephyr | xvfb
The following NEW packages will be installed:
  firejail
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 252 kB of archives.
After this operation, 866 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 firejail amd64 0.9.52-2 [252 kB]
Fetched 252 kB in 1s (446 kB/s)  
Selecting previously unselected package firejail.
(Reading database ... 206353 files and directories currently installed.)
Preparing to unpack .../firejail_0.9.52-2_amd64.deb ...
Unpacking firejail (0.9.52-2) ...
Setting up firejail (0.9.52-2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...

```

---

### Post by uRock on 2019-09-12
Rebooted and ran updates to see if it would tell me to uninstall stuffs and it didn't. Looks like I'm all good here. 

Thanks TheFu!

---

### Post by TheFu on 2019-09-12
You probably want firejail-profiles package too.  Check /etc/firejail/
From time to time, they make changes to allow certain issues to be resolved.

[https://github.com/netblue30/firejail/issues/1075](https://github.com/netblue30/firejail/issues/1075) explains why they added xvfb to the dependencies. It shouldn't be a default, IMHO.  I've used xvfb a few times on headless servers without any GPU to get some poorly written proprietary Oracle server software to work.

---

