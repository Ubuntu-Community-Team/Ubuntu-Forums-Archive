---
title: "gnone-speech-0.4.18 ./configure ORBit"
date: 2008-06-02
forum: General Help
---

### Post by ezufelt on 2008-06-02
Yesterday I installed Ubuntu and now I am trying to get the source of gnome-speech-0.4.18 compiled and installed.  Please find below the steps I have followed and my error message.
 
I would appreciate any assistance you can provide, or to know if there is currently a repository version of gnome-speech that I cannot find.
 
1. Ubuntu 8.04; linux-image-686
2. Downloaded and decompressed source for gnome-speech-0.4.18
3. apt-get install checkinstall
4. apt-get install g++
5. apt-get install orbit
6. Opened a gnome-terminal session.
7. Navigated to the extracted directory from gnone-speech-0.4.18
8. sudo ./configure
 
Error:
configure: error: Package requirements (ORBit-2.0 >= 2.3.94) were not met:
 
No package 'ORBit-2.0' found
 
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
 
Alternatively, you may set the environment variables ORBIT_CFLAGS
and ORBIT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
 
 
 
 
Thanks,

---

### Post by go_beep_yourself on 2008-09-27
You are supposed to install packages ending in dev for compiling so try installing liborbit2-dev and configure should stop complaining about orbit not found.

---

