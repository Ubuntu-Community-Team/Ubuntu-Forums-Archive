---
title: "todays updates, messed with Nvidia drivers"
date: 2007-02-09
forum: General Help
---

### Post by sleeperknight on 2007-02-09
I updated the edgy kernel today from 2.6.17-10 to 2.6.17-11 and its failing to start x server saying that nvidia kernel module is 1.0-8776 but i have 1.0 9746 installed in xorg file.  how do I fix this, is there a way i can reinstall the nvidia driver and fix it?

---

### Post by bollix47 on 2007-02-09
When it fails to load and goes to a prompt login using your user name and password.

Navigate to the folder containing the NVIDIA*.run file for that driver.

Then run 
```

sudo sh NVIDIA*.run
```

---

### Post by sleeperknight on 2007-02-09
> **bollix47 said:**
> When it fails to load and goes to a prompt login using your user name and password.

Navigate to the folder containing the NVIDIA*.run file for that driver.

 um,  I ran it off of sudo apt-get install nvidia-glx, so where where the nvidia file be located?

---

### Post by shane634 on 2007-02-09
If you can get to a command prompt without Xserver login in and type your password. Then we can use this code:

```
sudo nano /etc/X11/xorg.conf
```

  This will open your Xorg.conf file. Look through it till you see the "nvidia" part and change it to "nv" this will at least let you login in with the old driver.   Now get the envy script from this site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

  Click on it and let Gdebi install it. Now open up a terminal(Applications->Accessories->Terminal ) and put in:

```
sudo /etc/init.d/gdm stop
```

  This will log you out of the Xserver. Get to the command prompt login and password then type envy. This will open the envy script. Choose the option for the Nvidia drivers then press enter.  Envy will do its thing then you can exit envy and either reboot or type:

```
sudo /etc/init.d/gdm start
```

  This will restart the Xserver. Hope this helps.

---

### Post by bollix47 on 2007-02-09
[http://ubuntuforums.org/showpost.php?p=2130656&postcount=232](http://ubuntuforums.org/showpost.php?p=2130656&postcount=232)

---

### Post by sleeperknight on 2007-02-09
ok I got the nvidia drivers working again with envy but, still having trouble with getting beryl up and running properly, but in sure their will be a update sometime soon that will fix it, if I don't manage to get it working before that.

---

