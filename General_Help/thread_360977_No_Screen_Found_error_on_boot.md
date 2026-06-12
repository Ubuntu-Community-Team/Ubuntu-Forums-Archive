---
title: "No Screen Found error on boot"
date: 2007-02-13
forum: General Help
---

### Post by btomw on 2007-02-13
Alright, so I had a little bit of trouble installing Ubuntu, but that's mostly because I was trying to install it on my second harddrive and realized later that I was going about it the wrong way. Still, all things considered it was a pretty painless install. 

Afterwards, I used it for about a night before my friend suggested I install Beryll on my system. When I tried to do so, it told me to install xserver-xorg. So, through the package manager, I installed both. Everytime I tried to run Beryll, though, it would crash and revert back to the defualt Gnome interface. Boo to that. So I logged out and tried loggin back in. Big mistake.

From that point on I've been recieveing a "no screen found" error on boot with a wonderfully windows like blue screen. I'm running a GeForce4 mx 440 GPU and a dell monitor of some kind, if that helps...

---

### Post by dcstar on 2007-02-13
> **btomw said:**
> Alright, so I had a little bit of trouble installing Ubuntu, but that's mostly because I was trying to install it on my second harddrive and realized later that I was going about it the wrong way. Still, all things considered it was a pretty painless install. 

Afterwards, I used it for about a night before my friend suggested I install Beryll on my system. When I tried to do so, it told me to install xserver-xorg. So, through the package manager, I installed both. Everytime I tried to run Beryll, though, it would crash and revert back to the defualt Gnome interface. Boo to that. So I logged out and tried loggin back in. Big mistake.

From that point on I've been recieveing a "no screen found" error on boot with a wonderfully windows like blue screen. I'm running a GeForce4 mx 440 GPU and a dell monitor of some kind, if that helps...

CTRL-ALT-F1, log in, then:
sudo dpkg-reconfigure xserver-xorg

---

### Post by btomw on 2007-02-13
I've reconfigured it several times and it hasn't worked. I did a great deal of research to find the solution and still don't know it. Are there any log files that might help someone help me?

---

### Post by interurban on 2007-02-14
The issue is most likely with your drivers.  You could download the Nvidia drivers if this is the case:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run
```and then install them:
```
sudo sh NVIDIA-Linux-x86-1.0-pkg1.run
```Make sure that at the end you tell it to configure your xorg.conf. Those are proprietary.  The beryl website has a great guide for installtion here: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
[This thread]("http://www.ubuntuforums.org/showthread.php?t=272104") has more information about installing beryl: [http://www.ubuntuforums.org/showthread.php?t=272104](http://www.ubuntuforums.org/showthread.php?t=272104)

---

