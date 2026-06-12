---
title: "nVidia drivers won't load at startup"
date: 2007-10-29
forum: General Help
---

### Post by Arun985 on 2007-10-29
Hi

I just got Ubuntu Gutsy installed, and now I'm trying to cofigure it to work with my nVidia Geforce 6200 card. I used Envy to install the nVidia drivers, and it seems like everything worked out pretty well, except when I restarted my computer with my monitor connected to my nVidia card, Ubuntu freezes on startup. When I reboot into Ubuntu from with my onboard graphics drivers, the OS goes into "low graphics mode." It seems like my system recognizes and wants to use the new nVidia drivers, but just won't load it at startup. How would I go about fixing this?

---

### Post by taurus on 2007-10-29
Edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and replace the "**nvidia**" with "**nv**".  Now, connect your monitor to your nVIdia graphic card and boot from it.  After you've logged in, click

System -> Administration -> Restricted Drivers Manager and enable nvidia driver from there.

---

### Post by Arun985 on 2007-10-29
Hi,

Thanks for your reply. I tried what you suggested, and I'm still in the same place. Ubuntu just won't load the nVidia drivers at startup and gets stuck the loading screen. Any other suggestions would be very helpful. Thanks.

---

### Post by taurus on 2007-10-29
Did you modify your /etc/X11/xorg.conf?  Otherwise, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Arun985 on 2007-10-29
Hi

Thanks for your suggestion. I went through the whole reconfiguration process and after I restarted my machine, with my monitor connected to my nVidia card, Ubuntu still gets stuck at the loading screen. Maybe Ubuntu is just not supposed to work for me. :( idk. Suggestions are still welcome.

---

### Post by taurus on 2007-10-29
Which driver did you pick?  Try using** vesa** driver for now until you get your machine back up again.  Then, install nVidia driver for your graphic card.

---

### Post by Arun985 on 2007-10-29
The driver isn't the issue. I used Envy to install the nVidia drivers, and it seems to be fine. Thing is, its just refusing to load at startup. Damn Defiant Drivers! :P

---

### Post by The Noble on 2007-11-01
There seems to be a problem with using custom nvidia drivers, which is conflicting with bullet proof x. I recently recompiled my kernel and it is refusing to detect the drivers I installed despite working with the version from the repos on my old kernel.

---

### Post by Arun985 on 2007-11-03
I'm still battling with this same problem. A lot of good solutions have been suggested, all of which I tried, but none have been successfull for me. When I try to boot Ubuntu Gutsy w/ my nvidia card, it doesn't ever get past the loading screen.

Any suggestions are still welcome.

---

### Post by magd1319 on 2008-05-02
I have the same problem exactly. Whenever I load up I can't get the nvidia drivers to work. 

The only way i can get something normal-ish working is just delete my xorg.conf and let xrandr take care of it (probably bad practice). Whatever I do, I can't get the nvidia drivers to load. 

This is particularly annoying for me since I have two monitors connected to my nvidia 7300GT via the dvi and vga ports, so i need to use the proprietary drivers.

Please help!

Dan

---

