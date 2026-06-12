---
title: "wrong display resolution using nvidia geforce 8400gs"
date: 2008-07-07
forum: General Help
---

### Post by zl2k on 2008-07-07
hi, there
I got the trouble that the screen is set to the save mode (800*600) after I tried to enable 3D for the nvidia geforce 8400gs. It was good before.
Now I disable the 3D (System->Administration->Hardware drivers) in nividia but still can't go back.
The system pop up a configuration screen each time I boot up and it does not pass the test for my configuration. So I can only use the safe mode in low resolution.
There is no other choice in System->Preferences->screen resolution I can choose.

Please help: How can I configure the monitor correctly? How can I setup nvidia graph card correctly? How can I enable its 3D if possible? 
Thanks for help.

zl2k

---

### Post by iaculallad on 2008-07-07
Had you tried:

```
sudo nvidia-settings
```

or

```
sudo nvidia-xconfig
```

---

### Post by zl2k on 2008-07-07
> **iaculallad said:**
> Had you tried:

```
sudo nvidia-settings
```

I did that and got the following message
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

or

```
sudo nvidia-xconfig
```

I did that and got the following message
> Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


I restart the system but nothing changed.

---

### Post by ellgor on 2008-07-08
Hi, 

Try this, check to see if you have a package called nvidia-settings (synaptic) install if not, once thats done open a terminal and type in "gksudo nvidia-settings" dont use the quotes, a new window will open with the settings for nvidia for you to play with, adjust as necessary, hope this helps.

Regards, Ellgor.

---

