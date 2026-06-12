---
title: "Both aptitude and apt-get hangs"
date: 2008-03-23
forum: General Help
---

### Post by Tex-Twil on 2008-03-23
Hello,
I have a problem with aptitude and apt-get cos they hangs when I try to install a packgage:

apt-get :
```

root@igloo:/etc/openvpn# apt-get install openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  resolvconf
The following NEW packages will be installed:
  openvpn
0 upgraded, 1 newly installed, 0 to remove and 50 not upgraded.
Need to get 0B/341kB of archives.
After unpacking 1020kB of additional disk space will be used.


```

Aptitude:

```

root@igloo:/etc/openvpn# aptitude install openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a kdesktop kfind kicker libavcodec1d 
  libavformat1d libavutil1d libiso9660-4 libkadm55 libkonq4 libkrb5-dev libpostproc1d libvlc0 linux-libc-dev 
  vlc-nox 
The following packages have been kept back:
  evolution evolution-common evolution-plugins firefox firefox-gnome-support konqueror language-pack-en 
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libcdio6 libkrb53 libnautilus-extension1 
  libpcre3 libpcrecpp0 libvolume-id0 linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic 
  linux-image-2.6.22-14-generic nautilus nautilus-data python2.5 python2.5-minimal tzdata ubuntu-docs udev unzip 
  vlc volumeid xserver-xorg-video-intel 
The following NEW packages will be installed:
  openvpn 
0 packages upgraded, 1 newly installed, 0 to remove and 50 not upgraded.
Need to get 0B/341kB of archives. After unpacking 1020kB will be used.
Writing extended state information... Done


```
And then nothing happens. In this example I'm trying to install opnevpn but the problem happens for any package I try to install.

I did apt-get update.

Im on Ubutnu Gusty.

Thanks
Tex.

---

### Post by pointone on 2008-03-23
Does this happen for any package? Try installing something else; it may just be openvpn.

Also, try running "apt-get clean" to clear out the cached package.

---

### Post by Tex-Twil on 2008-03-26
> **pointone said:**
> Does this happen for any package? Try installing something else; it may just be openvpn.

Also, try running "apt-get clean" to clear out the cached package.

Hello,
it is the same with all packages even if I run apt-get clean.  :

> root@igloo:/home/jan# apt-get clean
root@igloo:/home/jan# apt-get install iperf
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  iperf
0 upgraded, 1 newly installed, 0 to remove and 53 not upgraded.
Need to get 46.4kB of archives.
After unpacking 184kB of additional disk space will be used.
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe iperf 2.0.2-2 [46.4kB]
Fetched 46.4kB in 0s (102kB/s)
an then nothing happens  :confused:
 
Tex

---

