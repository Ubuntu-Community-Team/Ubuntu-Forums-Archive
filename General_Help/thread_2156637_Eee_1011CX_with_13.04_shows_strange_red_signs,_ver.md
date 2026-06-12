---
title: "Eee 1011CX with 13.04 shows strange red signs, vertical rainbow lines after waking"
date: 2013-06-22
forum: General Help
---

### Post by aronstandley on 2013-06-22
[COLOR=#333333][FONT=UbuntuRegular]I'm running Ubuntu 13.04 (Gnome) on an asus eee 1011cx. Whenever I close the lid without shutting down, then open it again, I get a series of what seems to me to be red characters across the top of the screen, followed a few seconds later by a screen full of vertical multicolored bars. I've not been able to get any other screen that this without restarting the computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What can I do to explore or solve this so that putting the computer to sleep and waking it again function by resuming the apps that were open before sleep?[/FONT][/COLOR]

---

### Post by searchfgold6789 on 2013-06-22
It looks like you have an Intel graphics card ... In my experience, these drivers have been very stable.
Maybe you could try the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")?

---

### Post by fantab on 2013-06-22
If I am not mistaken you have Cedartrail PowerVR chip. Though its shipped by Intel, the manufacturer is Imagine Technologies or someone (don't remember it). The driver is poorly supported in Linux. However there are ways and means to get it going but still the graphics performance is just basic. 

[URL="http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/"]http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/
[/URL][http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/)

I have 1015CX eee, and I have installed Fedora18_xfce_32bit and most of the things work out of the box. It seems fedora has some support for GMA3600 through GMA500. However, the experience with HD graphics is poor.

If you seach the WWW with terms 'cedarview', 'PowerVR', and 'GMA3600' you will understand what I am talking about.

Good Luck...

---

### Post by aronstandley on 2013-06-24
> **fantab said:**
> The driver is poorly supported in Linux. However there are ways and means to get it going but still the graphics performance is just basic. 

[URL="http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/"]http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/
[/URL][http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/)

Thanks for telling me about what the components are that contribute to this happening, I'm glad to know a bit more about the hardware end, and how ubuntu is interacting with it.

I'm a bit nervous to try running the commands in these links you shared - I have no idea about how 12.04 solutions would affect the 13.04 OS, or how to approach this problem with anything more than a trial-by-fire approach. Would you tell me if you think I should just plug one set or the other in, as-is, or if you think I should do something else before/during/after?

---

### Post by aronstandley on 2013-06-24
> **searchfgold6789 said:**
> Maybe you could try the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")?

Thanks for the suggestion :) . I'm not sure what this ppa is about, or what it does, and I didn't see anything about it that I understood from this link you shared. Could you describe how you think it would help this problem?

---

### Post by fantab on 2013-06-24
> **aronstandley said:**
> Thanks for telling me about what the components are that contribute to this happening, I'm glad to know a bit more about the hardware end, and how ubuntu is interacting with it.

I'm a bit nervous to try running the commands in these links you shared - I have no idea about how 12.04 solutions would affect the 13.04 OS, or how to approach this problem with anything more than a trial-by-fire approach. Would you tell me if you think I should just plug one set or the other in, as-is, or if you think I should do something else before/during/after?

Those methods in the links work. But you must install 12.04. I haven't tried 13.04 on my netbook. However, installing Ubuntu on eee with those methods needs maintainence. Why don't you try the OS I am using on my netbook, most of the things work out of the box. The only issue I had was that the tapping on touchpad was not working but we have a small workaround to get it running.

[https://spins.fedoraproject.org/xfce/](https://spins.fedoraproject.org/xfce/) 
To enable 'tapping' on touchpad: [URL="https://thangnguyennang.wordpress.com/2012/06/24/howto-enable-tapping-xfce-on-fedora-17/"]https://thangnguyennang.wordpress.com/2012/06/24/howto-enable-tapping-xfce-on-fedora-17/
[/URL]

---

### Post by aronstandley on 2013-06-24
Fantab:

Okay, it sounds like to make those solutions work, 12.04 is the way to go.

I have had 13.04 on it now, for about 2 weeks - do you know if is this not compatible with the solutions you shared?

The challenge for me with switching OS's now (ie to fedora or others) is that I have Raring up and (mostly) running now, have experience with gnome and Ubuntu, and have other commitments for my time that I'd rather focus on than learning and setting up a new OS. Even keeping the setup I have now, with the sleep problem, is preferable to me than switching to a new linux distro. For me, it's a big plus that this system works, can connect to the internet, and can start growing a simple audio production environment. Getting the sleep function fixed would be a big bonus.

To me now, it looks like bringing these 12.04 solutions to my 13.04 setup is the option that seems closest to being able to work, but even with this I'm not confident it will work. What comes to mind for you, hearing all this?

---

### Post by fantab on 2013-06-24
NO, I don't know if those solutions are compatible with 13.04. I haven't tried to install Ubuntu on my netbook since. So I can't help you any further.

Do you have 1GB RAM or 2GB? If you have 2GB then gnome-shell/Unity will run alright. But if you have only 1GB then XFCE (Xubuntu) or LXDE (Lubuntu) is the way to go as they are much lighter on system resources than the former DEs. 

Anyways, I think the soulution [HERE]("http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/") should work for you (though the ppa is for 12.04, try changing 'precice' to 'raring' in the ppa line), and it is simpler as well. If it doesn't work on 13.04 then you must install 12.04.
Just note that the solution uses 'VI' as the text editor, you just replace 'VI' with 'gedit' or 'nano', if you don't know how to use 'Vi'.
Here is the ppa at lauchpad: [URL="https://launchpad.net/~sarvatt/+archive/cedarview"]https://launchpad.net/~sarvatt/+archive/cedarview
[/URL]
Good Luck....

---

### Post by aronstandley on 2013-06-24
> **fantab said:**
> I think the soulution [HERE]("http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/") should work for you (though the ppa is for 12.04, try changing 'precice' to 'raring' in the ppa line), and it is simpler as well. If it doesn't work on 13.04 then you must install 12.04.
Just note that the solution uses 'VI' as the text editor, you just replace 'VI' with 'gedit' or 'nano', if you don't know how to use 'Vi'.
Here is the ppa at lauchpad: [URL="https://launchpad.net/~sarvatt/+archive/cedarview"]https://launchpad.net/~sarvatt/+archive/cedarview
[/URL]
Good Luck....

Okay, so I got this far.

```
aron@SV108-Aron:~$ sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package cedarview-drm
E: Unable to locate package libva-cedarview-vaapi-driver
E: Unable to locate package cedarview-graphics-drivers

```
Do you think this is a 13.04 issue or is this more with the server the packages are stored on? What do you think about where to go from here?

---

### Post by searchfgold6789 on 2013-06-26
> **aronstandley said:**
> Okay, so I got this far.

```
aron@SV108-Aron:~$ sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package cedarview-drm
E: Unable to locate package libva-cedarview-vaapi-driver
E: Unable to locate package cedarview-graphics-drivers

```
Do you think this is a 13.04 issue or is this more with the server the packages are stored on? What do you think about where to go from here?

Hi,
Something is wrong with your software source files. You or a program you installed probably put something there that apt does not like. 
For now, you should probably run ```
sudo rm -rfv /etc/apt/sources.d/*
```and then try the other command again.

---

### Post by fantab on 2013-06-27
> **searchfgold6789 said:**
> Hi,
Something is wrong with your software source files. You or a program you installed probably put something there that apt does not like. 
For now, you should probably run ```
sudo rm -rfv /etc/apt/sources.d/*
```and then try the other command again.

+1

After removing /etc/apt-sources.d/ with the above command run update again:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers
```

---

### Post by aronstandley on 2013-06-28
> **searchfgold6789 said:**
> run ```
sudo rm -rfv /etc/apt/sources.d/*
```and then try the other command again.
[COLOR=#000000]After removing /etc/apt-sources.d/ with the above command run update again:[/COLOR]
[COLOR=#000000]Code:

sudo apt-get updatesudo apt-get upgrade [/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers[/FONT][/COLOR]

Okay, here's what I got:

I ran
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo rm -rfv /etc/apt/sources.d/*
```
and got no response.

I ran
```
sudo apt-get update
```
and got this at the end of a long list of installing files:
```
[/FONT][/COLOR]N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extensionW: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/sarvatt/cedarview/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Then, I ran
```
sudo apt-get upgrade
```
and got this after a lot of lines of 'setting up X application':
```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

Then I ran the next one, and this is all the code I got back:
```
aron@SV108-Aron:~$ sudo apt-get install cedarview-drm libva-cedarview-vaapi-driver cedarview-graphics-drivers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package cedarview-drm
E: Unable to locate package libva-cedarview-vaapi-driver
E: Unable to locate package cedarview-graphics-drivers
```

What do you think is going on that these packages are unable to be located?

---

### Post by Rob Sayer on 2013-07-05
I've been through all this with my atom 2600/cedarview netbook in both 12.04 and 13.04.

None of those above links are relevant to 12.04 anymore, let alone 13.04.  For example, from launchpad.net/~sarvatt/+archive/cedarview:

> These packages are now in 12.04 in multiverse as of 8/17/2012, please don't use this PPA.



The cedarview driver packages were integrated properly into linux kernel v.3.7.  In ubuntu terms that means 13.04.  I'm not surprised the OP is having trouble installing that stuff.  It's not relevant for 13.04 so why put it in the repos?

So I don't think the OP's original question is necesssarily related to the ubuntu drivers, but unfortunately I don't have any ideas on that one.

I agree that installing ubuntu with the unity desktop isn't a good idea on a 1Gb netbook.  I originally installed in on my i3 based laptop with 4Gb RAM.  It was too slow on that so I yanked it, and I run kubuntu on both machines.  I've used xubuntu as well but xfce is not much faster than kde, and the lack of features slows me down.

---

### Post by aronstandley on 2013-07-15
> **Rob Sayer said:**
> I've been through all this with my atom 2600/cedarview netbook in both 12.04 and 13.04.

None of those above links are relevant to 12.04 anymore, let alone 13.04.  For example, from launchpad.net/~sarvatt/+archive/cedarview:



The cedarview driver packages were integrated properly into linux kernel v.3.7.  In ubuntu terms that means 13.04.  I'm not surprised the OP is having trouble installing that stuff.  It's not relevant for 13.04 so why put it in the repos?

So I don't think the OP's original question is necesssarily related to the ubuntu drivers, but unfortunately I don't have any ideas on that one.

Thanks for sharing your experiences with this Rob :) This helps me understand much more clearly what was going on when I tried those installations.

Please consider this post closed from my end of involvement. I don't want to spend my time trying to find answers to the multitude of software/hardware challenges that came up for me with Ubuntu, so I'm heading to Windows for the time being.

I want to thank everyone who shared their thoughts and advice with this problem of mine - I'm grateful for the support I got!

---

