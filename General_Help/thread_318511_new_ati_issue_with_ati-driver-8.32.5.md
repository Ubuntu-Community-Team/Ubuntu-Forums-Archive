---
title: "new ati issue with ati-driver-8.32.5"
date: 2006-12-14
forum: General Help
---

### Post by mirr0r on 2006-12-14
Hi,

I tried new ati driver version 8.32.5 and it doesn t work ](*,). 
I followed this how to (work perfect with version 8.31.5):

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

but with new driver:

```
web@notebook:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 1.5 Mesa 6.5.1

web@notebook:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
99 frames in 5.0 seconds = 19.800 FPS

```

I think the problem is this (from my Xorg.log):
```
(EE) AIGLX error: dlopen of /usr/lib/dri/fglrx_dri.so failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: XF86DRIGetDrawableInfo)
(EE) AIGLX: reverting to software rendering
```

Someone know how to solve this error?

Thanks, 
MiRr0r
PS I will never buy ati (now amd..) products!

---

### Post by newbie2 on 2006-12-14
maybe they (AMD/ATI) take notice if you post your 'issues' [here at their Linux Crew Driver Feedback]("http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web")

---

### Post by thechanklybore on 2006-12-14
Don't know the exact reason for this, but I can tell you that for a start Proprietary ATI Driver doesn't work with AIGLX (which has it's own set of drivers for OpenGL X Acceleration).
Your X server seems to be trying to start with AIGLX, which is certainly a problem.

I have just installed 8.32.5 using these instructions:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-85e9c413c70677bc07d04d8fd0afe4452028d472](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-85e9c413c70677bc07d04d8fd0afe4452028d472)

This works for me fine on Dapper using stable Xorg and XGL/Beryl.

P.S Although ATI driver support seems a bit lacking in Linux, there's nothing wholly wrong with the driver or the product - in fact I get just as good framerates for gaming etc as I used to in Win XP.

---

### Post by mirr0r on 2006-12-14
> **newbie2 said:**
> maybe they (AMD/ATI) take notice if you post your 'issues' [here at their Linux Crew Driver Feedback]("http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web")


Ok, I submit my feedback..

> P.S Although ATI driver support seems a bit lacking in Linux, there's nothing wholly wrong with the driver or the product - in fact I get just as good framerates for gaming etc as I used to in Win XP.

Mmm.. I think you don t have my notebook:
**Msi M635: ** amd turion 64 mt-34; 512 mb ram; ati X700; 80 gb hard disk; 15,4' TFT;
Just one little example: when I boot with an ubuntu 6.10 livecd, my monitor come black: I must open an other shell, change xorg.conf with vesa driver, restart x....](*,) 
this is a little frustrating but I love linux so.. :mrgreen: :mrgreen: I m here!!

thanks, Mirr0r

---

