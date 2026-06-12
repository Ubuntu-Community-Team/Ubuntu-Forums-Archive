---
title: "GL screensavers slow, except with XGL/Beryl"
date: 2006-11-04
forum: General Help
---

### Post by chadjohnson on 2006-11-04
Hi all

In both Dapper and Edgy, I've found that with ATI proprietary fglrx drivers correctly installed, GL screensavers have always been slow. Hardware acceleration is enabled for sure - fgl_glxgears works, and glxinfo says "direct rendering: yes."

However, when I installed XGL on Dapper and now Beryl on Edgy the screensavers work 10 times better. Anyone else experience this, and anyone know what causes this?

Note that with Beryl running glxinfo says "direct rendering: no."

Here is the Module section of my xorg.conf file:
```

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

```

--

BTW, been using Ubuntu for the last 6 months and it's been absolutely great! I don't like using Windows when I have to now :p

---

### Post by jungleb on 2006-12-04
Hey ... the same thing happens to me ... and really don't know what should be the issue for this ... I'm not on Beryl so that shouldn't be ... something on fglrx drivers ... 
btw I've installed this one:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually")

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Right now I'm busy trying to make totem stop crashing xserver every time I want to watch some video :twisted: 

Later I'll try to figure out why gl screenies get slow with fglrx.

Feel free to msg me ...
cya!

---

