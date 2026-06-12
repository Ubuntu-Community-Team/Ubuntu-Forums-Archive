---
title: "Empty placeholders for Googleearth pictures."
date: 2015-11-11
forum: General Help
---

### Post by makem2 on 2015-11-11
```

makem@newTOSH:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
makem@newTOSH:~$ xfce4-session --version
xfce4-session 4.12.1 (Xfce 4.12)

Copyright (c) 2003-2014
    The Xfce development team. All rights reserved.

Please report bugs to <http://bugs.xfce.org/>.
makem@newTOSH:~$

```

 [TABLE]
[TR]
[TD] Google Earth[/TD]
[TD] 7.1.4.1529[/TD]
[/TR]
[TR]
[TD] Build Date[/TD]
[TD] 3/30/2015[/TD]
[/TR]
[TR]
[TD] Build Time[/TD]
[TD] 10:42:27 pm[/TD]
[/TR]
[TR]
[TD] Renderer[/TD]
[TD] OpenGL[/TD]
[/TR]
[TR]
[TD] Operating System[/TD]
[TD] Linux (3.13.0.0)[/TD]
[/TR]
[TR]
[TD] Video Driver[/TD]
[TD] Intel Open Source Technology Center[/TD]
[/TR]
[TR]
[TD] Max Texture Size[/TD]
[TD] 8192x8192[/TD]
[/TR]
[TR]
[TD] available video memory[/TD]
[TD] information not available
[/TD]
[/TR]
[TR]
[TD] Server[/TD]
[TD] kh.google.com[/TD]
[/TR]
[/TABLE]


When I first installed googleearh, if I clicked on a picture link on the map, a picture opened up.

I have made several updates to the system and at some stage I lost this facility and now just see an empty placeholder. In addition, googleearth seems to crash more often when clicking on a picture link or sometimes when making a place search.

Would it be my settings which are causing this?

---

### Post by HappyAsHellas on 2015-11-14
This has been an ongoing problem for a while now. There was a solution posted somewhere on here but it didn't work for me. I came across this on a Linux Mint forum which brings up the photos as you would expect. However, I have to run google earth from the terminal and whilst it's running I get a lot of error messages in the terminal itself, although the program works fine. If you want to, just run these commands:

 	sudo apt-get install libc6:i386 lsb-core

 

  	wget -O google-earth64.deb [http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb](http://drive.noobslab.com/data/apps/google-earth/google-earth_amd64.deb)


  	sudo dpkg -i google-earth64.deb


  	rm google-earth64.deb


  	sudo apt-get install libfreeimage3


  	cd /opt/google/earth/free


  	sudo wget [https://googledrive.com/host/0B2F__nkihfiNalQzN0ZmcjBPTGs/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz](https://googledrive.com/host/0B2F__nkihfiNalQzN0ZmcjBPTGs/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz)


  	sudo tar xvf ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz


  	sudo apt-get install gufw


  	sudo apt-get install flashplugin-installer

Don't ask me exactly what these commands mean as I'm not certain, but the program now works for me on Ubuntu 14.04lts

---

### Post by makem2 on 2015-11-14
Thanks but if you don't know why it works then if I get a problem..............

---

