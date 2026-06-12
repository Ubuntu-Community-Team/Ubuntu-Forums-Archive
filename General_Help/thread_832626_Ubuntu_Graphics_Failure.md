---
title: "Ubuntu Graphics Failure"
date: 2008-06-17
forum: General Help
---

### Post by Techrocket9 on 2008-06-17
After upgrading the Linux kernel and the drivers on my Ubuntu computer, the computer goes into a graphics resolution that my monitor can not display at the login screen. I uninstalled everything nVidia. Now the computer will load in 800x600 mode only. There is no option to change the resolution. After following every graphics repair tutorial on the internet, the nVidia drivers will install, but not boot with the computer. After some of the tutorials, the drivers appear in the restricted drivers thing under system. Enableling them and rebooting does not actually load them. All help is greatly appreciated.

---

### Post by unutbu on 2008-06-17
I'm not sure if I can help you, but would you please post 

```
sudo lshw -C video
COLUMNS=150 dpkg --list nvidia*
```

Also, have you tried each of the following?
```

sudo dpkg-reconfigure -phigh xserver-xorg
gksudo displayconfig-gtk
gnome-display-properties
sudo nvidia-settings
```

---

### Post by manimal347 on 2008-06-17
Have you set the drivers to actually load in your xorg.conf, found at /etc/X11/xorg.conf? You need to change your listed "device" (graphics card) to say "nvidia." 

Having your xorg.conf would in general be helpful.

---

### Post by Techrocket9 on 2008-06-25
Another automatic update fixed the problem. Thanks anyway. ):P

---

