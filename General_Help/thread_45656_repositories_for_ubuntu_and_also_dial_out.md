---
title: "repositories for ubuntu and also dial out"
date: 2005-07-01
forum: General Help
---

### Post by cobelloy on 2005-07-01
hi there, just installed ubuntu and got a couple a Q's about repositories:

I have added the nerim.net repositories to the list and it tells me -

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

are the repo's still being used? And, the reason I added them was so I could get dvd::rip (and transcode). I just switched from mepis and it was those repo's that had dvd rip, I did apt-get install dvdrip and all was cool, but with ubuntu (apt-get or synaptic I can't get transcode, it is listed on the synaptic list, but I get this -

transcode:
 Depends: libavcodeccvs but it is not going to be installed
 Depends: libavifile-0.7c102 but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libgcc1 (>=1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed

Also, I have configured my modem with wvdial from the commandline, I have made a modem group so I can dial out as normal user, but can't I just use some kind of gui thing to dial out (like kppp?)

sorry if I ask the same Q's over again, I did a qick search, but I am a little busy.

thx in advance

---

### Post by Xian on 2005-07-01
The nerim.net repos are not recommended for general use in Ubuntu as the Backport repos, which can easily be [enabled](http://ubuntuguide.org/#extrarepositories) on you system, have most of what you would be looking for and are more compatible with the Hoary release. The error you were receiving are not a local issue, and as such would need to be addressed with that maintainer.

---

### Post by cobelloy on 2005-07-01
OK, I got rid of the nerim repo's and followed the instructions at the link and now I am gettin dvdrip (and all the other stuff too)

thanks for that, anyone know what to use for dial out instead of using wvdial from the terminal?

also -

having trouble playing video files with totem, I keep getting a message that says no codecs are available (for all types, mpeg's and avi's), I already did apt-get install w32codecs, do I need something else ? I did find a few threads on this so if it is just too common a Q I can just search properly later

thnx

---

### Post by PMO6022 on 2005-07-01
[QUOTE=cobelloy]having trouble playing video files with totem, I keep getting a message that says no codecs are available (for all types, mpeg's and avi's), I already did apt-get install w32codecs, do I need something else ? I did find a few threads on this so if it is just too common a Q I can just search properly later
 
[/QUOTE]
 
Try searching here: [http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by cobelloy on 2005-07-01
[QUOTE=PMO6022]Try searching here: [http://ubuntuguide.org/]("http://ubuntuguide.org/")[/QUOTE]
 yep, that took care of the video, 

thanks :)

---

