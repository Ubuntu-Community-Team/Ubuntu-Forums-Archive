---
title: "Startup and shutdown splash screen is in low resolution"
date: 2008-04-25
forum: General Help
---

### Post by timzak on 2008-04-25
Just did a fresh install of 8.04 final and noticed that the startup and shutdown splash screens (ubuntu logo) are in a low resolution (oversized and pixellated).  This is a brand new, clean install.  Here's a recap of my install and some other issues that might be related:

1)installed from scratch
2)changed resolution from 1920x1440 (my monitor's max) to 1600x1200.  Everything is great.
3)changed to nvidia restricted driver and rebooted--ended up in 1280x1024 after reboot!
4)went back to resolution changer and noticed that 1280x1024 is now the highest resolution available.  I changed it to 1280x960 to get my ratio back to 1.33. (I realize I can fix this easily by editing xorg.conf, but why isn't the nvidia driver seeing my other resolutions?)
5)at this point I noticed the ubuntu splash being oversized and pixellated when I was shutting down and starting up.  So I'm not sure when it actually started, but I noticed it at this point.

Any ideas?  Nothing too serious, just makes me feel like something's not quite right with the install.

Thanks.

---

### Post by chrisccoulson on 2008-04-25
You can specify the resolution in /etc/usplash.conf - just edit the xres and yres values to values supported by your monitor, then do:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by timzak on 2008-04-26
Thanks, but I don't know how to format this.  There are no examples in the usplash.conf file.  Also, I never had to do this in Feisty or Gutsy, why now in Hardy?

---

### Post by 6205 on 2008-04-26
You can fix this with installation of startup-manager where you can choose resolution for splash...But it's shame that it is another step back from Gutsy...

---

