---
title: "Fresh Ubuntu 14.04 LTS install slow"
date: 2014-04-18
forum: General Help
---

### Post by RookieUbuntuUser58 on 2014-04-18
Specs of my Ubuntu box:
Pentium 4 @ 3ghz
ATI Radeon X600/X600SE (RV370)
1GB RAM
1GB Swap

This isn't my main computer but just something I like to test Linux distros on. 

It ran 12.04.4 LTS smoothly. That was with many more installed applications. 

Fresh install of 14.04 LTS not so smooth. No issue with boot up or logging in. Its when you enter the desktop. Opening applications, tabs in google chrome, minimizing windows and even simply installing an app from the software center. It freezes for quite awhile sometimes. I already reduced the swappiness to 10. 

Is 14.04 LTS more memory hungry? Anything I can do? Is there a proprietary driver for the GPU needed?

---

### Post by frank18 on 2014-04-18
> **RookieUbuntuUser58 said:**
> Specs of my Ubuntu box:
Pentium 4 @ 3ghz
ATI Radeon X600/X600SE (RV370)
1GB RAM
1GB Swap

This isn't my main computer but just something I like to test Linux distros on. 

It ran 12.04.4 LTS smoothly. That was with many more installed applications. 

Fresh install of 14.04 LTS not so smooth. No issue with boot up or logging in. Its when you enter the desktop. Opening applications, tabs in google chrome, minimizing windows and even simply installing an app from the software center. It freezes for quite awhile sometimes. I already reduced the swappiness to 10. 

Is 14.04 LTS more memory hungry? Anything I can do? Is there a proprietary driver for the GPU needed?

Open Software Manager, in the settings manager check if you have additional drivers
also you better use firefox,also there are some broken packages that you can keep trying to update,eventually it will fix itself, remember this is the 2 day of the release, i'm sure ubuntu is working on it.
also make sure your pc will handles Ubuntu well,Xubuntu is also a great choice

---

### Post by RookieUbuntuUser58 on 2014-04-18
> **frank18 said:**
> Open Software Manager, in the settings manager check if you have additional drivers
also you better use firefox,also there are some broken packages that you can keep trying to update,eventually it will fix itself, remember this is the 2 day of the release, i'm sure ubuntu is working on it.
also make sure your pc will handles Ubuntu well,Xubuntu is also a great choice

I actually checked Software Manager but it turns up no additional drivers. Interesting you bring up Firefox, I immediately dumped it for Chrome. Broken packages?

---

### Post by grahammechanical on 2014-04-18
Actually, I found 14.04 to be using less RAM than 12.04. How much memory does the graphic adapter have? That I think is the key question. Back in the days of 12.04 if the graphic adapter was incapable of running Unity 3D then Unity 2D was installed. That option is no longer available. With 14.04 the desktop will load using a version of the open source video driver to try to give a representation of Unity 3D. It is called llvmpipe. If that is running things may indeed seem slow and you may get better results with a proprietary video driver.

Regards.

---

### Post by RookieUbuntuUser58 on 2014-04-18
> **grahammechanical said:**
> Actually, I found 14.04 to be using less RAM than 12.04. How much memory does the graphic adapter have? That I think is the key question. Back in the days of 12.04 if the graphic adapter was incapable of running Unity 3D then Unity 2D was installed. That option is no longer available. With 14.04 the desktop will load using a version of the open source video driver to try to give a representation of Unity 3D. It is called llvmpipe. If that is running things may indeed seem slow and you may get better results with a proprietary video driver.

Regards.

Manufacturer site shows GPU memory size at 128 MB.

---

### Post by RookieUbuntuUser58 on 2014-04-19
Still need help with this.

---

### Post by Mengsk91 on 2014-08-09
**Rookie**, I'm installing Ubuntu 14.04 again. I was having the same problem, and everything just crashed when I change the video drivers from xorg to nvidia. 
When I sort this mess up, I'll share my experiencie. Hang on!

BTW I've seen the date of your message. Did you have any improvements?

---

