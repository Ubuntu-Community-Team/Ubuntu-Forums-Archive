---
title: "Intel Graphics Drivers Installation Issue Ubuntu 15.10 Willy"
date: 2016-03-24
forum: General Help
---

### Post by David_Berger on 2016-03-24
So Im new to Ubuntu and this forum so let me know if this question is in the wrong catagory. Anyways I was trying to install the Intel graphics driver for Ubuntu 15.10, however I keep getting this message which I also get when updating my system.

W:GPG error: [https://download.01.org](https://download.01.org) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A496EB03894A3A8D, W:Failed to fetch [http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Does anyone know what I need to do to fix this? 

Thank you

---

### Post by Uinthe on 2016-03-24
Show 
ls -l /etc/apt/source.list.d/
Also u dont have a correct key to use download.01.org rep.

UPD. If u follow any link u posted, u will get
> **Not Found**

 The requested URL /falk-t-j/qtsixa/ubuntu/dists/wily/main/binary-i386/Packages was not found on this server.


It means that these reps are not supported or its just a host problem. In the first case u should delete these reps from /etc/apt/source.list.d/ . Otherwise try to update a bit later.

---

