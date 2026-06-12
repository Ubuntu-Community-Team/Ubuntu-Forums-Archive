---
title: "ubuntu 14.02 crash"
date: 2016-07-28
forum: General Help
---

### Post by dave241 on 2016-07-28
I have a Fresh install of unbuntu 14.04lts and it crashes every time I load FireFox or try to update it.
I was reading a forum post on downgrading the OS to 12.04 or changing the OS to lubuntu.

pc is a stock hp pavilion entertainment pc
3gb ram 
AMD Turion(tm) 64 X2 Mobile Technology TL-60 × 2 
GeForce 7150M / nForce 630M/integrated/SSE2
64-bit OS

I just want my pc to be able to run any help would be apreciated

screenshot of the error

---

### Post by sudodus on 2016-07-28
1. First you can try the newest version, ***16.04.1 LTS*** of a lighter flavour of Ubuntu, for example ***Lubuntu***, ***Xubuntu*** or ***Ubuntu MATE***, that will probably work better with your hardware. I have a computer with an AMD Athlon of similar age, and it works well with this version and these flavours.

```
     *-display
          description: VGA compatible controller
          product: C68 [GeForce 7050 PV / nForce 630a]
          vendor: nVidia Corporation
```

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

2. I suggest that you try with the boot option nomodeset, that helps run the nvidia graphics in a basic mode. Then (in the installed system) you can try to install a proprietary nvidia driver and reboot.

See this link: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

3. Only if problems with 16.04.1 LTS I suggest that you try with an older version. Notice that Ubuntu 12.04 LTS will pass end of life in April 2017, and the lighter flavours have already passed end of life, and will no longer receive any security updates.

---

### Post by grahammechanical on 2016-07-28
The newest Nvidia drivers do not supported older Nvidia video adapters. But the Additional Drivers utility may offer an older, legacy Nvidia driver.

Ubuntu with the Unity user interface really needs a video adapter that can do hardware accelerated 3D rendering. If the video adapter cannot run Unity 3D and an alternative video driver is used that will give an approximation of Unity 3D. I can seem slow. But things have improved with Ubuntu 16.04.1

> **Low graphics mode **

An interesting improvement for users of older hardware, those who might  access their machines over a remote-desktop connection or users of  virtual machines. We have been working on improving the optimisations  for lower powered graphics hardware or software backed rendering. The  Unity 7 desktop makes use of modern graphics hardware to display desktop  components such as the dash and to provide visual enhancements to the  daily operation of the desktop. In order to speed up the rendering of  the desktop on less powerful machines we have reduced or removed a lot  of the animations and blur effects. Low graphics mode has always been  included in Unity 7 but we are now a being a bit more aggressive when it  comes to disabling some of these effects. Unity 7 will automatically  detect if your hardware is supported for the full experience and if not  it will enable low graphics mode. Users can also manually enable low  graphics mode but those instructions are beyond the scope of this post  and will be followed up in a separate post. Keep an eye on the usual  social media channels for more information.

[http://insights.ubuntu.com/2016/07/28/ubuntu-version-16-04-point-1-is-out/](http://insights.ubuntu.com/2016/07/28/ubuntu-version-16-04-point-1-is-out/)

Do not have too high an expectation with that hardware. Xubuntu, Lubuntu or Ubuntu Mate might give you a better experience as recommended in other posts. But if you do want to use Ubuntu then 14.04.1 will be a lot better experience than older versions. Especially over 12.04.

Regards

---

### Post by dave241 on 2016-07-29
so I changed my graphics driver to a proprietary version and updated everything but Firefox and the PC hasn't crashed all night. maybe tomorrow I will attempt to update and load Firefox. I'll update the status in the AM also, I do the 16.04 on a boot-drive if the need arises. as for a browser I don't get what feels like a memory leak from chromium that I get from FF right before the PC freezes.

---

### Post by dave241 on 2016-07-29
so I updated Firefox and the PC crashed. it is just sitting with a black screen with a mouse curser. attempting to see if I can restore to a earlier date(20 min ago)

**Update**
Restoring back to fresh install.

So glad i haven't done anything on this pc outside open up the internet on chromium or id be upset for the data loss.

---

### Post by sudodus on 2016-07-29
Maybe it was caused by the proprietary driver. If you have to use the free 'nouveau' driver, standard Ubuntu might demand too much from the graphics, and you might get much better performance with a lighter Ubuntu flavour (less demanding graphical desktop environment).

- Lubuntu, ultra light or
- Ubuntu-MATE and Xubuntu , medium light.

---

### Post by dave241 on 2016-07-29
> **sudodus said:**
> Maybe it was caused by the proprietary driver. If you have to use the free 'nouveau' driver, standard Ubuntu might demand too much from the graphics, and you might get much better performance with a lighter Ubuntu flavour (less demanding graphical desktop environment).

- Lubuntu, ultra light or
- Ubuntu-MATE and Xubuntu , medium light.

I tried it with the default driver and propritary drivers and the result is the same.
It seems if i dont use FF or attempt to update it, i have no issues

---

### Post by sudodus on 2016-07-29
I understand what you write, but I don't understand why this happens, why you have problems with firefox. Can you use another web browser, or in general, other graphical application programs? Could it be that the graphics is overloaded, for example because Ubuntu wants 3D graphics, and the old graphics chip cannot provide it?

Please try with a lighter desktop environment - for example try Lubuntu live (without installing), only 'Try Lubuntu'.

---

### Post by dave241 on 2016-07-30
> **sudodus said:**
> I understand what you write, but I don't understand why this happens, why you have problems with firefox. Can you use another web browser, or in general, other graphical application programs? Could it be that the graphics is overloaded, for example because Ubuntu wants 3D graphics, and the old graphics chip cannot provide it?

Please try with a lighter desktop environment - for example try Lubuntu live (without installing), only 'Try Lubuntu'.

i will try that tomorrow when my buddy comes back over with the bootdrive. he accidentally took it with him. i can use chromium with no issues.

side note ubuntu 16.04 cant connect to wifi, seems like a lot of people have that issue. going back to 14.04 today. i have never reloaded an OS this many times in my life then i have the last 3 days. im serious, 20ish fresh re installs. hah love bug testing trying to find something stable for my pc

---

### Post by dave241 on 2016-07-31
lununtu 16.04 works great so far

---

### Post by dave241 on 2016-07-31
> **sudodus said:**
> I understand what you write, but I don't understand why this happens, why you have problems with firefox. Can you use another web browser, or in general, other graphical application programs? Could it be that the graphics is overloaded, for example because Ubuntu wants 3D graphics, and the old graphics chip cannot provide it?

Please try with a lighter desktop environment - for example try Lubuntu live (without installing), only 'Try Lubuntu'.

So far everything is working
day 2 on lubuntu 16.04 and no lag problems and no crashing.
Looks like we can call this problem solved

thanks,
Dave

---

### Post by sudodus on 2016-08-01
I'm glad Lubuntu works for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

