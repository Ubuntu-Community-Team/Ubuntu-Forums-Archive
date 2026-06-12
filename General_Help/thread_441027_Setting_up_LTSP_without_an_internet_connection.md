---
title: "Setting up LTSP without an internet connection"
date: 2007-05-12
forum: General Help
---

### Post by strayduck_uk on 2007-05-12
I'm using [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) as a guide to getting LTSP set up on my desktop which is running Ubuntu Server 7.04. The reason? I just want to play :-) and the technology maybe useful for a couple of projects I am working on.

Unfortunately, as with many other 7.04 users, my rt2500 USB based wireless device is not working, and I can't currently run a length of CAT5 into my desktop, so I am without internet. I've edited my /etc/apt/sources.list file so that I can use packages off the server CD and I've been successful down to the command

```
sudo ltsp-build-client
```

At which point apt-get dumps with the error "Failed getting release file" followed by a URL for what I'm guessing is a remote repository.

Do I need to add another line to my sources.list file to point to another place on the CD? If not, is it possible to download the appropriate package from the repo, burn it to another CD, and then install it from that CD?

Alternatively, if anyone has succeeded in getting the rt2500 to work in 7.04 then let me know, its odd because the device is recognised and you can give it iwconfig and iwlist commands but it doesn't seem to be able to find any networks, secured or otherwise.

Thanks in advance.

---

### Post by SpiritIsReality on 2007-11-01
howdy
as for the no internet connection, and the ltsp-build-client this is the best I can come up with. It looks as though you can point the build command to the cdrom as a mirror. If there
is a package missing, then have to go after it. Have a look at these links and see if that's what you reckon.
[http://ubuntuforums.org/showthread.php?t=327360](http://ubuntuforums.org/showthread.php?t=327360)
[http://www.uluga.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2640291](http://www.uluga.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2640291)
> D.) Built the ltsp client in the same xterm (I only use i386 clients with my amd64 server):
ltsp-build-client --dist etch --arch i386
Optional, you can use your own mirror (or local mirror) with an additional parameter (e.g. this is my local mirror, you have to pick another one):
ltsp-build-client --dist etch --arch i386 --mirror [http://192.168.0.11/mirrors/etch](http://192.168.0.11/mirrors/etch)
The ltsp-build-client script needs a lot of time (especially with a non local mirror).
E.) If you want to have local device access you need some Debian Sid (= Debian unstable) packages. These packages are at the moment not available for Etch (as of april 2007). Don't care about "unstable", they worked fine for me.
Point your favorite browser to:
[http://packages.debian.org/unstable/net/ltspfs](http://packages.debian.org/unstable/net/ltspfs)
and get the package for your server (!!!) architecture (for me it is amd64 = ltspfs_0.4.3+debian2_amd64.deb).
Then go for: [http://packages.debian.org/unstable/net/ltspfsd](http://packages.debian.org/unstable/net/ltspfsd)
and get the package for your clients (!!!) architecture (for me it is i386 = ltspfsd_0.4.3+debian2_i386.deb)
F.) Install the ltspfs server (!!!) package:
In an xterm as root go to the just downloaded ltspfs server package and type (remember, amd64 is my server architecture, you may have another one):
dpkg -i ltspfs_0.4.3+debian2_amd64.deb
G.) Copy the ltspfsd client package into your chroot: In an xterm as root go to the just downloaded ltspfsd client (!!!) package and type:
cp ltspfsd_0.4.3+debian2_i386.deb /opt/ltsp/i386/root
H.) Now we do some action in the chroot:
You are root and type in an xterm:
chroot /opt/ltsp/i386
From now you are in the client environment (!!!), go to:
cd /root
and there install the client ltspfsd package:
dpkg -i ltspfsd_0.4.3+debian2_i386.deb

as for the usb wirless card it looks like it should be possible?
[http://www.google.ca/search?as_q=rt2500+usb&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=rt2500+usb&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

maybe an edubuntu dual boot? They have extra cd's and different install setup, where the ltsp is installed as part of the initial installation.
[http://www.google.ca/search?hl=en&q=site%3Aedubuntu.org+extra+cd&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aedubuntu.org+extra+cd&btnG=Google+Search&meta=)
[http://www.edubuntu.org/](http://www.edubuntu.org/)

other pages
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22ltsp-build-client%22+&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22ltsp-build-client%22+&btnG=Search&meta=)
[http://ubuntuforums.org/showthread.php?p=3637124](http://ubuntuforums.org/showthread.php?p=3637124)

trails

---

### Post by SpiritIsReality on 2007-11-02
howdy
any chance here for the belkin usb?
[http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=belkin+usb&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=belkin+usb&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
trails

---

### Post by Lem on 2007-11-11
Have the install cd in the drive and use;

```
sudo ltsp-build-client --mirror file:///cdrom
```

You might need to delete your old build first;

```
sudo rm -rf /opt/ltsp/i386
```

---

### Post by SpiritIsReality on 2007-11-11
howdy
Good Answer. I wish I knew that. But I guess I do NOW! thanks!
trails

---

### Post by zahris on 2007-11-23
i tried to create an ltsp VIA local repositories.. but on my gutsy gibbon's ltsp installation the "--mirror" option is unavailable..

so is there anyone know how to configure it manually.. 

thx b4

---

### Post by Dragonbite on 2007-12-06
> **Lem said:**
> Have the install cd in the drive and use;

```
sudo ltsp-build-client --mirror file:///cdrom
```

You might need to delete your old build first;

```
sudo rm -rf /opt/ltsp/i386
```

Very helpful! Thanks.

---

