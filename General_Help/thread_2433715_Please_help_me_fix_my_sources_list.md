---
title: "Please help me fix my sources list"
date: 2019-12-24
forum: General Help
---

### Post by sah0724 on 2019-12-24
I got a bunch of stuff installed that's messing up my updates, please help me out. I was about to go back to windows and stick with a linux VM. I'm running unbuntu 19.04 but it's problems... I'm mainly fairly new at linux.


```
sudo apt update
Ign:1 cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco InRelease
Err:2 cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:4 [Index of /ubuntu]("http://archive.canonical.com/ubuntu")  disco InRelease                                                                                                                                                   
Hit:5 [Index of http://download.virtualbox.org/virtualbox/debian]("http://download.virtualbox.org/virtualbox/debian")  eoan InRelease                                                                                                                                       
Hit:6 [Index of /ubuntu]("http://us.archive.ubuntu.com/ubuntu")  disco InRelease                                                                                                                                                   
Ign:7 [Index of /ubuntu]("http://archive.canonical.com/ubuntu")  multiuniverse InRelease                                                                                                                                           
Get:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb)  stable Release [943 B]                                                                                                                                           
Ign:9 [Index of linux/ubuntu/]("https://download.docker.com/linux/ubuntu") eoan InRelease                                                                                                     
Err:10 [Index of /ubuntu]("http://archive.canonical.com/ubuntu") multiuniverse Release                                                                     
  404  Not Found [IP: 2001:67c:1562::1c 80]
Get:11 [Index of /ubuntu]("http://us.archive.ubuntu.com/ubuntu") disco-updates InRelease [97.5 kB]                                                         
Get:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]                                                                           
Hit:13 [Index of /gns3/ppa/ubuntu]("http://ppa.launchpad.net/gns3/ppa/ubuntu") eoan InRelease                                                                                               
Hit:14 [Index of linux/ubuntu/]("https://download.docker.com/linux/ubuntu") disco InRelease                                                             
Get:15 [Index of /ubuntu]("http://security.ubuntu.com/ubuntu") eoan-security InRelease [97.5 kB]                             
Hit:16 [Index of /ubuntu]("http://archive.ubuntu.com/ubuntu") eoan InRelease                                                             
Err:17 [Index of linux/ubuntu/]("https://download.docker.com/linux/ubuntu") eoan Release                                                       
  404  Not Found [IP: 2600:9000:21f2:b800:3:db06:4200:93a1 443]
Hit:18 [Index of /ubuntu]("http://archive.ubuntu.com/ubuntu") eoan-updates InRelease                                                     
Get:19 [Index of /ubuntu]("http://us.archive.ubuntu.com/ubuntu") disco-backports InRelease [88.8 kB]
Ign:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg         
Err:13 [Index of /gns3/ppa/ubuntu]("http://ppa.launchpad.net/gns3/ppa/ubuntu") eoan InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9A2FD067A2E3EF7B
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository '[Index of /ubuntu]("http://archive.canonical.com/ubuntu") multiuniverse Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'partner/binary-1386/Packages' as repository '[Index of /ubuntu]("http://archive.canonical.com/ubuntu") disco InRelease' doesn't support architecture '1386'
E: The repository '[Index of linux/ubuntu/]("https://download.docker.com/linux/ubuntu") eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb)  stable Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 6494C6D6997C215E
E: The repository '[http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used. GPG error: [Index of /gns3/ppa/ubuntu]("http://ppa.launchpad.net/gns3/ppa/ubuntu")  eoan InRelease: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 9A2FD067A2E3EF7B
W: Skipping acquire of configured file 'stable/source/Sources' as repository '[Index of linux/ubuntu/]("https://download.docker.com/linux/ubuntu") disco InRelease' does not seem to provide it (sources.list entry misspelt?)
N: Skipping acquire of configured file 'main/binary-1386/Packages' as repository '[Index of /ubuntu]("http://archive.ubuntu.com/ubuntu") eoan InRelease' doesn't support architecture '1386'
N: Skipping acquire of configured file 'universe/binary-1386/Packages' as repository '[Index of /ubuntu]("http://archive.ubuntu.com/ubuntu") eoan InRelease' doesn't support architecture '1386'
N: Skipping acquire of configured file 'universe/binary-1386/Packages' as repository '[Index of /ubuntu]("http://archive.ubuntu.com/ubuntu") eoan-updates InRelease' doesn't support architecture '1386'
N: Skipping acquire of configured file 'main/binary-1386/Packages' as repository '[Index of /ubuntu]("http://archive.ubuntu.com/ubuntu") eoan-updates InRelease' doesn't support architecture '1386'
N: Skipping acquire of configuhttps://dl.bintray.com/aluxian/red file 'universe/binary-1386/Packages' as repository '[Index of /ubuntu]("http://security.ubuntu.com/ubuntu") eoan-security InRelease' doesn't support architecture '1386'
N: Skipping acquire of configured file 'main/binary-1386/Packages' as repository '[Index of /ubuntu]("http://security.ubuntu.com/ubuntu") eoan-security InRelease' doesn't support architecture '1386'
```

---

### Post by mörgæs on 2019-12-24
Hi, welcome to the fora.

Are you sure it's worth the while to salvage 19.04 which has only one month of support left? You could consider to use the occasion to do a fresh install of 19.10 (a nice Christmas gift for yourself).

---

### Post by sah0724 on 2019-12-24
Okay the grub isn't working, my laptop can't find a boot default and won't recognize the usb... how can I fix this?

I installed gns3 and I had to dl extra packages and that's what happened.

---

### Post by sah0724 on 2019-12-25
I think this was the problem.

f you would like to allow GNS3 support for  IOS on Unix (IOU), you&#8217;ll have to enable running of x86 packages on a 64-bit system.     sudo dpkg --add-architecture i386
sudo apt-get update

---

### Post by mörgæs on 2019-12-25
Good, please mark the thread solved (top right corner, thread tools).

---

