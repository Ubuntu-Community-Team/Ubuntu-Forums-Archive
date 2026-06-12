---
title: "No Gnome X Session"
date: 2008-01-21
forum: General Help
---

### Post by Malthus25 on 2008-01-21
Hi, I've been having a problem with my Gnome Session. Upon advice from one of the threads here (that I can't find now), I tried uninstalling and reinstalling gnome-session. It completely borked my system. When I boot up, I get the standard Ubuntu boot screen, then in flips to a low-res text boot screen and asks for a login. When I login and try to run gnome-session, it tells me that it can't open the display.

As to my old problem, I think it may have been an NVidia driver issue. It was working fine for months, and then my taskbars weren't displaying properly and the only icon on them that worked was the Trash Can. In addition, I wasn't getting any sound out of my system.

I'd like to fix this without having to do a total reinstallation, if possible.

N.B.: While I'm not a total Unix newbie, I am not a sysadmin type; please spell out your suggestions in as simple terms as possible.

Thanks.

---

### Post by erpo on 2008-01-22
The quick solution is to back up your important data and reinstall. What? You're already backing up regularly? Awesome.

If you want to save time and inconvenience by fixing the problem directly rather than reinstalling, it's going to cost you something. TANSTAAFL. You could pay someone to do it for you, or you could spend more time learning about system administration. If you opt for the latter, you should start by reading /var/log/Xorg.0.log and looking for error messages.

FWIW, I consider myself up to the task of fixing a problem like the one you're describing, and I would still just reinstall. It's getting easier and easier every day.

---

### Post by geirha on 2008-01-22
If your login screen comes up in low res, then your xorg.conf is probably not quite right. Either edit /etc/X11/xorg.conf manually and try setting the driver in the "Device"-section to "nv" which I believe is the open-source nvidia driver, or do "sudo dpkg-reconfigure xserver-xorg"

---

### Post by Malthus25 on 2008-01-22
geirha, the login screen isn't coming up lo-res. I'm not getting the normal graphical login at all; I'm getting a text login.

erpo, the only error I can find in the Xorg log is the last line. The last 5 lines are:

 "(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:05:0
(WW) VESA: No matching Device section for instance (BusID PCI:0:5:0) found
(EE) No devices detected
Fatal server error: no screens found".

Any idea what this means?


BTW, thank both of you for trying to help.

---

### Post by Malthus25 on 2008-01-22
Okay, I tried what geirha said, and it partially worked. I got to the normal login screen after it said that it was running in lo-res and asked me if I wanted to configure. I tried configuring once and tried continuing once, same result.

So, I tried logging in at the standard login screen and it let me in, then hung at a blank screen with a mouse pointer. 

What do I do now?

---

### Post by geirha on 2008-01-23
I don't know really. I have very little experience with nvidia cards, so if neither the nv-driver nor the vesa-driver will work, I'm not sure what will. How did you install the nvidia drivers earlier btw? By using the restricted drivers manager?

You might have some luck with upgrading and reconfiguring all packages. If this is caused by a broken package, this will hopefully fix it.
```
sudo aptitude update
sudo aptitude safe-upgrade
sudo dpkg-reconfigure -a
```
It will take a long time, and it may ask you some questions on some packages.

---

