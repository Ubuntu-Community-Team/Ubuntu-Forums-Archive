---
title: "Maya 2014 on Ubuntu 13.10"
date: 2013-11-26
forum: General Help
---

### Post by GregPayne on 2013-11-26
I have been trying to get Maya 2014 student edition to work on Kubuntu 13.10. I found a nice script which installed it, or at least seamed to. However when actually running the application i get the following error.

In case the information is needed i have attached a copy of the script i used to install Maya. 

gregpayne@payne-MS-7522:~$ maya


libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.


maya encountered a fatal error


Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/gregpayne.20131126.1253.ma
Segmentation fault (core dumped)
gregpayne@payne-MS-7522:~$ 


Can anyone point me in the right direction to resolve this issue.

---

### Post by mikewhatever on 2013-11-29
Check where swrast is with **locate swrast**. In my case, the location is '/usr/lib/i386-linux-gnu/dri', but yours may be different.

Then try running 'export LIBGL_DRIVERS_PATH=/usr/lib/i386-linux-gnu/dri'.

---

