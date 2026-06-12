---
title: "NVidia and XServer"
date: 2004-12-16
forum: General Help
---

### Post by gdeswardt on 2004-12-16
So I installed my NVidia drivers for my DELL Inspiron 8200 laptop as specified in [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) and after rebooting GDM does not load up any more. Getting a message saying that the X-Server config is not valid and disabled it until the settings are correct.

So when I am trying to login in text mode it would not accept my username and password at all. This is the same username and password I used withing GDM to login.

Any ideas suggestions would be much appreciated.


G

---

### Post by gdeswardt on 2004-12-16
When I start up machine under Ubuntu (Recovery Mode) and try to execute 

```
sudo dpkg-reconfigure xserver-xfree86
``` 

I get the following error message

```
No such pseudo-hash field "l" at /usr/share/perl5/Debconf/Config.pm line 35, <DEVCONF_CONFIG> chunk1
```

Any help would be much appreciated

---

### Post by bube on 2004-12-16
If you install nvidia-glx, you need to run "**nvidia-glx-config enable**" or manually edit your X config. 
```
Section "Device"
	Identifier	"somenvidiacard"
	Driver		"**nvidia**"
	BusID		"PCI:1:0:0"
``` 
Make sure that you are useing "nvidia". Also read [this](http://www.ubuntulinux.org/wiki/BinaryDriverHowto). It discribe this in detail.

---

### Post by gdeswardt on 2004-12-17
as mentioned in my first post I did read the the thread of how to NVidia, so I did run ```
nvidia-glx-config enable
``` but when I try and configure the xserver I get the error mentioned in my second post

---

### Post by gdeswardt on 2004-12-17
even if i execute nvidia-glx-config enable i still get the same error

```
No such pseudo-hash field "l" at /usr/share/perl5/Debconf/Config.pm line 35, <DEVCONF_CONFIG> chunk1
```

---

### Post by Totzo on 2004-12-17
Hi,

I'm pretty new to this but have got my nvidia drivers working by installing the restricted module from hoary and using "module-assistant" (apt-get install module-assistant) then editing the xorg.conf file. My copy of doom3 still doesn't work though. Any ideas anyone?

---

### Post by dr.diesel on 2004-12-19
After I installed ubuntu I passed unofficial started guide in FAQs section of this forum  and the driver works - BTW it worked with nv too, but i changed to nvidia. But the graphics seem very slow to me. On Windows, the process of fading by logout or by minimizing the window goes very quick, but in linux it takes a while and it's quite annoying me - Duron 700, GF4 MX440 - nothing excellent, but for fast "window moving" it should be enough IMHO.

The worse thing is, when I logout from desktop manager (Gnome for now), the graphic login doesn't change the resolution and displays only a part of screen - not scrollable. The login screen has 1600x1200 - quite useless - in Gnome I use 1152x868@100Hz - the prob with resolution and freq solved using Xfree86 modelines from LiveCD  :roll: but it works well.

---

### Post by dr.diesel on 2004-12-22
no suggestions? ;-)

---

### Post by ArtificialSynapse on 2007-05-15
Can you just post your whole /etc/X11/xorg.conf file here?

---

