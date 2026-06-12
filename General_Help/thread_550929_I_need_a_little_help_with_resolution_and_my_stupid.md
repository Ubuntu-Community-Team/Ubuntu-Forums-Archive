---
title: "I need a little help with resolution and my stupid Dell 4600c..."
date: 2007-09-14
forum: General Help
---

### Post by spotdog14 on 2007-09-14
Hello everyone. I have been running Ubuntu on my laptop for about a year now, and have it on various other computers in my home now. So i have become fairly familiar with it. But for the life of me i cannot figure out WTF is wrong with my work computer. First off i cannot boot off of the Ubuntu livecd, any of them. So i download the debian windows installer and i install debian that way, and it actually worked. But now my problem is that i cannot get the resolution to change. 

I have the resolutions i want added into /etc/X11/xorg.conf but it still defaults to 640x480. The computer has an Intel 82865G Integrated graphics device that shows up correctly and its connected to a Dell e772c CRT. It is capable of running 1280x1024 at 32 bit depth, but i cannot for the life of me get it to work. I have all the resolutions taken out of all the display modes accept for 1280x1024 and 1024x768.

Any ideas guys?

---

### Post by kuja on 2007-09-14
I'm hoping what you mean by the "debian windows installer" is the ubuntu alternate cd, and I'm hoping you're using the latest (feisty).

I *think* there's a package called "xserver-xorg-video-intel" in the Feisty Universe repository, if not, it could be in backports. Anyhow, it has much improved support for intel gpus, so it could be worth a shot.

```

sudo apt-get update
sudo apt-get remove xserver-xorg-video-i810
sudo apt-get install xserver-xorg-video-intel

sudo dpkg-reconfigure xserver-xorg
```

When reconfiguring X, be sure to select the "intel" driver.

---

### Post by tmetzcc325 on 2007-09-14
Hey, I have an 82845G graphics chip and couldn't get my new widescreen monitor to run at its native 1440x900 resolution, but found this post that got me up and running with it...maybe it can help you too...

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Good luck,
Tom

---

### Post by spotdog14 on 2007-09-14
> **kuja said:**
> I'm hoping what you mean by the "debian windows installer" is the ubuntu alternate cd, and I'm hoping you're using the latest (feisty).

I *think* there's a package called "xserver-xorg-video-intel" in the Feisty Universe repository, if not, it could be in backports. Anyhow, it has much improved support for intel gpus, so it could be worth a shot.

```

sudo apt-get update
sudo apt-get remove xserver-xorg-video-i810
sudo apt-get install xserver-xorg-video-intel

sudo dpkg-reconfigure xserver-xorg
```

When reconfiguring X, be sure to select the "intel" driver.

what i mean by the debian windows installer is that when you go to [http://goodbye-microsoft.com](http://goodbye-microsoft.com) the installer that lets you configure a linux install from windows before you re-boot. Well anyways it was the only thing i could get to work on this computer. 

But that is besides the point, its not ubuntu unfortunately because i cannot get ubuntu to work. 

Also i cannot find xserver-xorg-video-intel in any of the installed debian repos. if you let me know the repo address i can add it and then download it, and in theory at least it should work.

BTW thanks for the help!

---

### Post by tmetzcc325 on 2007-09-14
I think I just had universe and multiverse selected, and was able to find the package.  Try that link in my previous post, but if that doesn't work, then I don't know what to tell you :)

by the way, scroll all the way down to the heading that says "Well, it worked for me: Feisty, Intel i810 video & Widescreen LCD" for the part about the Intel chips...

---

