---
title: "Screen Resolution"
date: 2006-10-12
forum: General Help
---

### Post by ricanelite on 2006-10-12
How can I go about and fixing my Screen Resolution right now it is only displaying 1024x768. I know it could go higher than that. So please forgive me I'm a Linux Newbie, so please help me out the best way you can, Thank you so much!

---

### Post by gosh on 2006-10-12
> **ricanelite said:**
> How can I go about and fixing my Screen Resolution right now it is only displaying 1024x768. I know it could go higher than that. So please forgive me I'm a Linux Newbie, so please help me out the best way you can, Thank you so much!

Look at desktop settings. 

If the required resolution is not there you might want to reconfigure xserver:
```
sudo dpgk-reconfigure xserver-xorg
```
and follow the instructions. At one moment you are able to choose which resolutions your monitor is able to use. 

Or you could add the resolutions to your xorg.conf file. But first make a backup of that file, in case things go wrong:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
```

Changes will be effective after you restart Xserver. You can do this by pressing <ctr><alt><backspace> and login again.

---

