---
title: "Leaving ATI for NVIDIA"
date: 2007-01-21
forum: General Help
---

### Post by needlenose on 2007-01-21
Tired of trying to get ATI drivers working so just bought a GeForce 7600 GS OC. Do I need to remove my old drivers before taking out my old card, if so how? Yes I'm a newbie so detailed help is appreciated.
Thanks in advance.
Almost forgot I'm using Edgy

---

### Post by Ramses de Norre on 2007-01-21
Install the nvidia drivers, change your driver in xorg.conf, shut down, replace ati with nvidia card, boot. All should be fine then.
You can remove the ati drivers, but it isn't really necessary. They'll just remain installed but unused. (So logic thing is to remove them ;))

---

### Post by needlenose on 2007-01-21
> **Ramses de Norre said:**
> Install the nvidia drivers, change your driver in xorg.conf, shut down, replace ati with nvidia card, boot. All should be fine then.
You can remove the ati drivers, but it isn't really necessary. They'll just remain installed but unused. (So logic thing is to remove them ;))

Installed drivers, changed Xorg.conf, after changing cards and rebooting X would'nt start. I get to a black screen with cursor.
I am now running off of a old Knoppix live dvd.

Help please

---

### Post by jocko on 2007-01-21
> **needlenose said:**
> Installed drivers, changed Xorg.conf, after changing cards and rebooting X would'nt start. I get to a black screen with cursor.
I am now running off of a old Knoppix live dvd.

Help please

Run this command from the command line:
```
sudo dpkg-reconfigure xserver-xorg
```select the correct video driver and leave the other options as they are.
restart gdm by this command to see if it worked:
```
 sudo /etc/init.d/gdm restart
```

---

### Post by needlenose on 2007-01-21
Thank you, ran the code in Knoppix then restarted and I'm back!=D>

---

### Post by telmo on 2007-01-21
Although Nvidia has better support for linux, i would never change ATI for Nvidia. ATI is so much better...
Good luck with that anyway.

---

### Post by buckrodgers on 2007-01-21
I think that I will do the same as needlenose because I rather have a graphic card that works without problems.

For the time being ATI + Linux  = Problems ](*,)

---

### Post by sloggerkhan on 2007-01-21
I have an ATI card, and I think the open source driver is getting better....
This last time, all I had to do was add 2 lines to my xorg.conf
(Option		"Monitor layout" "LVDS, CRT"
	Option		"Meta modes" "640x480,1680,1050")
and it was working perfectly out of the box....
I'm even running beryl using AIGLX on it.

---

