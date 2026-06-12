---
title: "Installing X-FI, Can't Delete Files, HELP!"
date: 2007-10-29
forum: General Help
---

### Post by thepocketdrummer on 2007-10-29
First problem...

I can't seem to be able to install the X-Fi Beta drivers. I need them for some form of audio.

On Debian/Ubuntu, stock kernel :
```
# apt-get install module-assistant
# m-a prepare
# m-a update
```

- download driver from creative : [http://www.creative.com/language.asp?sDestUrl=/support/downloads](http://www.creative.com/language.asp?sDestUrl=/support/downloads)
- download [http://olausson.de/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch](http://olausson.de/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch) somewhere.
	   [http://blackbox.lostwave.net/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch](http://blackbox.lostwave.net/x-fi/XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch) (mirror)
- log as root

```
# tar -xvzf XFiDrv_Linux_US-1.04.tar.gz XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
# tar -xvjf XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
# chmod -R 755 XFiDrv_Linux_US-1.04
# find XFiDrv_Linux_US-1.04/ -exec touch -c {} \;
# patch -p0 < XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch
# cd XFiDrv_Linux_US-1.04
# ./configure
# make
# make install
```

Q: during "make install" I get: "./ctsound: 35: Syntax error: Bad substitution" 
A: If you are using Debian/ubuntu, your /bin/sh probably point to /bin/dash. 
---> Edit ctsound and change #!/bin/sh to #!/bin/bash 

Ok, so I did the whole thing and got this error. I fix the file like it says... still doesn't work. Retry the whole thing, then change ctsound after make and it gives me a different error.

Any suggestions? :confused:

Also, I can't delete any of the folders I was using because I put them in the Home folder and it won't let me empty the recycle bin when I try.

---

### Post by thepocketdrummer on 2007-10-30
No one knows how to fix this?

](*,)

---

