---
title: "Installing Nero Linux 3 Beta in 64bit Ubuntu 7.04"
date: 2007-05-15
forum: General Help
---

### Post by Ublis on 2007-05-15
Here's what I did to get it installed, with the help of the skype installation instructions found on the net and these forums. Perhaps someone else will find it useful.

All commands below are as sudo.

1. Download from [http://www.nero.com/eng/NeroLinux3Beta.html](http://www.nero.com/eng/NeroLinux3Beta.html)
2. Force installation: ```
dpkg --force-architecture -i nerolinux-3.0.0.0-beta-x86.deb
``` A menu item appears in *Sound & Video*.
3. ```
ldd /usr/bin/nero
``` gives all kinds of missing .so files that are in /usr/lib instead of /usr/lib32. Move them: 
```
mv /usr/lib/libNero* /usr/lib32/
mv /usr/lib/libNewTrf.so /usr/lib32/
mv /usr/lib/libCDCopy.so /usr/lib32/
```
It might be necessary to also move the /usr/lib/nero folder to /usr/lib32/nero - seem to be some audio converters, but the ripping and AudioCD-from-mp3 functionality is disabled AFAICT so no way to test. Burning an ISO worked OK.

---

### Post by JoWilly on 2007-05-24
Nerolinux 3 final was released today.  You can download the 32bit and the 64bit version on nero.com

---

