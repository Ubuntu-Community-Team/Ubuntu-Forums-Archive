---
title: "Any reason one should install the proprietary Nvidia drivers other than vdpau ?"
date: 2013-12-19
forum: General Help
---

### Post by linuxyogi on 2013-12-19
Hi,

Recently my graphics card went bad. It was a Nvidia 9500 GT which has vdpau capability. So I always used to install the nvidia proprietary driver right after installing Ubuntu.

Now I am using Nvidia onboard graphics which doesn't support vdpau.

I watch lots of high definition videos but I dont play any games.

After watching some videos on youtube about using only opensource software I am quite motivated and I no longer want keep any proprietary software installed unless necessary.

Do I need the proprietary driver ?

---

### Post by monkeybrain20122 on 2013-12-19
If you don't play games and don't need vdpau for hd video then I don't see why you can't just use the free driver. I find the free driver actually smoother for most normal desktop usage than the proprietary driver. I have never been able to adjust screen brightness with the proprietary driver but nouveau has always worked.

nouveau is good enough  even for quite a few opengl games like assault cube or gl-117.

I have an installation of Saucy on an external drive which has no proprietary driver (since I use it as portable), I find it smoother for most purposes than my installation in the internal drive that does have the Nvidia driver,--I want vdpau,-- when booting off the same laptop.

There are however a few glitches. 1) switching user is sometimes problematic, cursor freezes. 2) Chrome doesn't work with hardware rendering (so no webgl, e.g) If enable it manually then flash becomes unusable in full screen and often get black pages.

These are not show stoppers for me(There is only one user and I use Firefox 99% of the time), but maybe useful for your consideration. Also I am installing my free driver from [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/) for better performance, so some of the instability may be the result of that.

---

### Post by grahammechanical on 2013-12-19
I stopped using Nvidia drivers about a year ago when a combination of kernel, Xserver and Nvidia driver broke the development version of Ubuntu that I was running. I have several installs of Ubuntu. I test the install process. I never tick to install third party software as that brings in the Nvidia driver, which I have my suspicions about. I always get to a desktop on reboot. which is not always the case with Nvidia drivers. I have no problems running Ubuntu Trusty Tahr on a Nvidia GT220 using Nouveau. 

Regards.

---

### Post by VMC on 2013-12-19
I prefer *nouveau*, but using Ubuntu, Gnome and Xubuntu, it will freeze at times. Xubuntu will freeze everytime using Abiword. Gnome when I try the settings manager, and Ubuntu using Dash more than once. *Nouveau* is much smoother and quicker than nvidia, but I'm stuck. Only Kubuntu works without a hitch.

---

### Post by mc4man on 2013-12-19
> **VMC said:**
> I prefer *nouveau*, but using Ubuntu, Gnome and Xubuntu, it will freeze at times. Xubuntu will freeze everytime using Abiword. Gnome when I try the settings manager, and Ubuntu using Dash more than once. *Nouveau* is much smoother and quicker than nvidia, but I'm stuck. Only Kubuntu works without a hitch.

As far as Ubuntu - you could try using the "no blur" option for the Dash. Here I always did that on my nvidia laptop with nouveau. 
(not one for colors so with 'no blur' set the 'Background color' in unityshell plugin settings to a mid to high opacity using black.

The best thing here about nouveau on that laptop is it doesn't use 'powermizer' so card is always running at high speed

More Ot -  my current laptop has a nvidia 660m so for linux just use the intel side, works just great, don't miss nvidia at all. Can also get vdpau for intel thru some players when desired (mpv, mplayer), and also in Firefox for flash using the new libvdpau-va-gl1 & some setting changes

---

### Post by sgage on 2013-12-20
I find the nouveau drivers to be perfectly acceptable in the performance department with my GeForce 8500 GT card. However, my computer locks up upon resuming from suspend unless I use the nvidia drivers, so I always install them. YMMV - I think this problem might only exist for a handful of nvidia GPU versions.

---

### Post by linuxyogi on 2013-12-20
> **grahammechanical said:**
> I stopped using Nvidia drivers about a year ago when a combination of kernel, Xserver and Nvidia driver broke the development version of Ubuntu that I was running. I have several installs of Ubuntu. I test the install process. I never tick to install third party software as that brings in the Nvidia driver, which I have my suspicions about. I always get to a desktop on reboot. which is not always the case with Nvidia drivers. I have no problems running Ubuntu Trusty Tahr on a Nvidia GT220 using Nouveau. 

Regards.

Lately I am getting suspicious about all closed source software !

So, do yyou think reming the Nvidia proprietary driver will undo all the changes that its installation did to the system or do I need to do a fresh install of Xubuntu ?

---

### Post by philinux on 2013-12-20
> **linuxyogi said:**
> Lately I am getting suspicious about all closed source software !

So, do yyou think reming the Nvidia proprietary driver will undo all the changes that its installation did to the system or do I need to do a fresh install of Xubuntu ?

You can uninstall it anytime. Reboot then try out the system. You can reinstall it again anytime.

---

### Post by d-cosner on 2013-12-20
I have 13.10 installed on a computer with NVidea 6550 on-board graphics, the open source drivers are really working well these days! As a natter of fact, the open source Intel and ATI drivers are also working great too. The graphics on all 3 computers look great to me and I do not have to worry about breakage from updates. I do not play any games but my kids do on the computer with NVidea graphics, they seem happy with the pc and plymouth even displays nicely.

I used to have problems with the ATI and NVidea open source drivers, artifacts on start up and screen flicker but I have had no issues at all using 13.10. I do not have anything against using the closed source drivers and I do use them with PCLinuxOS but I do like how my Ubuntu installs are just working out of the box. Almost forgot, I used to have problems with the computer locking up using the open source NVidea drivers but that seems to be completely fixed with 13.10.

I like using the open source graphics drivers when ever possible because the developers are better able to support them and things like kernel updates, upgrades are less likely to create any problems.

---

### Post by buzzingrobot on 2013-12-20
In my experience, it's gonna depend on the hardware and what someone does with it. More demanding use in combination with a spiffy new Nvidia card probably demands the latest Nvidia driver. Routine desktop use and occasional Flash videos probably won't see an advantage coming from an Nvidia driver.

There's something to be said for using the simplest approach that delivers what you need.

---

### Post by VMC on 2013-12-20
I forgot to mention that *nouveau* freezes from Ubuntu 13.10 - Ubuntu 14.04 current testing. 12.04 works perfectly. Adding nvidia drivers will stop the freezing but cause choppy movement. The freeze is not immediate, but using system-settings or "too much" dash access. Once frozen, the screen usually ends up in a diagonal scrambled mess. No way to access any logs at that moment.

Unsure if its X or *nouveau* itself or some other graphic library.

---

### Post by linuxyogi on 2013-12-20
Uninstalled the proprietary driver. Played some 1080p videos using vlc and tested flash player in FF. No issues but I the entire display in general seems to lack brightness or contrast I am not sure.

With the proprietary driver in use the display was much brighter.

---

### Post by monkeybrain20122 on 2013-12-20
> **linuxyogi said:**
> Uninstalled the proprietary driver. Played some 1080p videos using vlc and tested flash player in FF. No issues but I the entire display in general seems to lack brightness or contrast I am not sure.

With the proprietary driver in use the display was much brighter.

I don't know if this is true in general, but in my experience (three different Nvidia cards on laptops) one cannot control the brightness of the screen if the Nvidia driver is installed, it is always at its brightest. But with noveau you can adjust with the keyboard. So maybe somehow the screen is set to go dim butit has no effect when the Nvidia driver was installed and now it is still in a dim state. You can try adjust the brightness key and see if it helps.

---

### Post by linuxyogi on 2013-12-20
> **monkeybrain20122 said:**
> I don't know if this is true in general, but in my experience (three different Nvidia cards on laptops) one cannot control the brightness of the screen if the Nvidia driver is installed, it is always at its brightest. But with noveau you can adjust with the keyboard. So maybe somehow the screen is set to go dim butit has no effect when the Nvidia driver was installed and now it is still in a dim state. You can try adjust the brightness key and see if it helps.

I have increased the brightness and contrast of my monitor to max but its still a bit on the lower side.

Anything I can do from within Xubuntu ?

---

### Post by linuxyogi on 2013-12-20
I just found this [http://askubuntu.com/questions/252628/cant-adjust-screen-brightness-on-ubuntu-12-04lts](http://askubuntu.com/questions/252628/cant-adjust-screen-brightness-on-ubuntu-12-04lts)

But when I do ```
$ xbacklight -set 50
No outputs have backlight property
 
```

---

