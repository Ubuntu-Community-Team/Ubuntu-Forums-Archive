---
title: "Why doesn't Ubuntu detect new hardware automatically?"
date: 2007-01-14
forum: General Help
---

### Post by Duffy on 2007-01-14
I put in a new video card yesterday. It seems that unlike Windoz, Ubuntu cannot automatically redetect a new video. The video card is Nvidia based. When I reboot it just comes up in text mode or like a server. In searching the forum here, all I can find are these Go-awful long instructions to edit this, replace that, etc. - went through some of the suggestions, but no luck.

If Ubuntu and other Linux distros are going to be successful for the average home user, the OS should automatically detect new hardware or hardware changes and make the appropriate changes on the OS side without much intervention by the user. If the video would have come up I could have manually adjusted things like the video resolution etc., but without the KDE environment coming up, working in a text environment only is the the best option.

Seems Linspire had a way of redetecting new hardware on start-up and making the required changes at the OS level. If that's true, Ubuntu should have the capability to do it also. Or does it and it just didn't work for me?

---

### Post by Sef on 2007-01-14
What exactly is your graphics card?

---

### Post by Duffy on 2007-01-14
Verto (PNY) GeForce FX5200. AGP 8X with 256MBs of on-board memory.

---

### Post by konst88 on 2007-01-14
I think this should do the trick:
```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by wpshooter on 2007-01-14
> **konst88 said:**
> I think this should do the trick:
```
sudo dpkg-reconfigure xserver-xorg

```

That will more than likely solve the problem.

But I agree with Duffy, this should be automatic.  At a maximum all the user should have to do is change the video driver back to some generic/standard driver before installing the new video card and then have to install the new video driver for his new card once he/she gets to the desktop.

---

### Post by konst88 on 2007-01-14
But I think it is a problem of X, not of ubuntu.

---

### Post by Duffy on 2007-01-14
I tried sudo dpkg-reconfigure xserver-xorg yesterday after that suggestion was posted elsewhere in the forum for another user. That did not work.  I am giving up and just going to reinstall Kubuntu and hope it detects the new video card.

---

### Post by konst88 on 2007-01-14
You may choose the vesa driver, which will always work.
Don't run to reinstall the system, it is not windows...

---

### Post by tribaal on 2007-01-14
Yeah choosing vesa should take care of the problem.
In case the driver is the problem, the NVIDIA dirvers can be installed from command-line with the follwing commands:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
chmod +x NVIDIA-Linux-x86-1.0-9746-pkg1.run
./NVIDIA-Linux-x86-1.0-9746-pkg1.run

```
This should let you install the latest (stable) NVIDIA drivers.
During the setup, you'll be asked if you want to "overwrite x config". You want to answer yes to this question (it'll configure X to work with your nvidia drivers)

Hopefully this should solve the problem.

If you're still stuck at a terminal after a reboot, try the following command and see if it helps:

```
sudo /etc/init.d/kdm start
```

Hope this helps :)

- trib'

---

### Post by Ramses de Norre on 2007-01-14
> **wpshooter said:**
> But I agree with Duffy, this should be automatic.  At a maximum all the user should have to do is change the video driver back to some generic/standard driver before installing the new video card and then have to install the new video driver for his new card once he/she gets to the desktop.

That's in fact how it is.. if you set your driver to vesa before swapping the cards you'll get x at startup and you can install the new drivers and restart x to get them working.
Of course if you don't set vesa before you reboot, you'll need to change your drivers from the command line...

---

### Post by yopnono on 2007-01-14
> **Duffy said:**
> I am giving up and just going to reinstall Kubuntu and hope it detects the new video card.

Do that, if you think that is the best way to handle the issue.
Or you could try to fix it and learn, but... what do I know ;)

---

### Post by zerhacke on 2007-01-14
If it's a newly installed system and you changed the video card without putting any real data or special configuration into the machine, there's no real harm in just reinstalling.

However, that's likely not the case as nobody switches video cards immediately after install unless they had a cooked video card and didn't know it.

I too suggest reconfiguring the machine by hand WITHOUT a reinstall.  You'll learn a lot about your system.

---

### Post by blackened on 2007-01-14
This is listed as an essential feature spec in Feisty. See [here]("https://launchpad.net/ubuntu/+specs") under Bulletproof X.

---

### Post by Jengu on 2007-01-14
> **konst88 said:**
> But I think it is a problem of X, not of ubuntu.

Well, X is responsible for video in Ubuntu, so it's Ubuntu's problem too.

As it turns out you were unlucky enough to choose the one piece of hardware where reconfiguration isn't automatic -- because the kernel loads hardware modules on demand every time at startup, it never even bothers storing some list of your current hardware like windows does. However, X isn't part of the kernel for better or for worse, and has a text configuration file. The Xorg developers are working on fixing this though -- future X releases will have no xorg.conf file at all, and everything will be setup automatically. But just so you know for the future, for just about anything else you can swap hardware in and out between boots without a peep out of Ubuntu.

---

### Post by konst88 on 2007-01-14
But this may couse the startup process much slower, starting to detect all hardware..

---

### Post by AusIV4 on 2007-01-14
> **konst88 said:**
> Don't run to reinstall the system, it is not windows...
I can't tell you how many times I've reinstalled Ubuntu, generally over relatively small issues I just got tired of dealing with. The great thing about Ubuntu though, is that it takes less than an hour and a half to reinstall my entire operating system **and** have it exactly as it was before the reinstall. With Windows, I only reinstalled once and it took the better part of my day. With Ubuntu I'm never afraid to try things that could screw up my system, because I can reinstall between my morning and afternoon classes. I find reinstalling on Ubuntu is a much more practical solution than it is on Windows. It certainly isn't the best solution in all cases, but I'm more willing to experiment than I was on Windows.

I might note that i do keep my home folder on a separate partition (which is several hundred gig), and I back up my root filesystem before reinstalls so I can quickly grab config files and stuff.

---

