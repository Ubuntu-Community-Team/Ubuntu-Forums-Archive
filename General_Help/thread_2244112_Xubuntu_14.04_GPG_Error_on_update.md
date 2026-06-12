---
title: "Xubuntu 14.04 GPG Error on update"
date: 2014-09-13
forum: General Help
---

### Post by manuleka on 2014-09-13
```

sudo apt-get update
....
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:20 http://nz.archive.ubuntu.com trusty InRelease                           
100% [20 InRelease gpgv 13 B] [Connecting to nz.archive.ubuntu.com (202.7.6.10)Splitting up /var/lib/apt/lists/partial/nz.archive.ubuntu.com_ubuntu_dists_trustyIgn http://nz.archive.ubuntu.com trusty InRelease                              
E: GPG error: http://nz.archive.ubuntu.com trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)

```

can someone tell me what this really means? this happens straight after a fresh installation...

update:
```

slackit@slackuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.1.4-0ubuntu14.04.1) but it is not going to be installed
       Depends: libqtcore4 (>= 4:4.8.0) but it is not installable
       Depends: libqtgui4 (>= 4:4.8.0) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.10) but it is not installable
       Depends: libtar0 but it is not installable
       Depends: libva-x11-1 (> 1.3.0~) but it is not installable
       Depends: libvlccore7 (>= 2.1.0) but it is not going to be installed
       Depends: libxcb-keysyms1 (>= 0.3.9) but it is not installable
       Recommends: vlc-plugin-notify (= 2.1.4-0ubuntu14.04.1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.1.4-0ubuntu14.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
slackit@slackuntu:~$ 

```

i can't seem to install any package... keeps reporting unmet dependecy issues
how can there be broken packages? this is a fresh install? could it be the image? I have tried redownloading xubuntu 14.04 image and still the same problem... :(

---

### Post by Toz on 2014-09-13
Looks like [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) is down. Try using a different server. See: [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by manuleka on 2014-09-15
yea you're right Toz - server is back now cheers :)

---

