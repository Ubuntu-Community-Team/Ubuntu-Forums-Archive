---
title: "Problem w/ nvidia driver after moving system."
date: 2007-01-10
forum: General Help
---

### Post by MeathooK427 on 2007-01-10
After bringing my box to work to try and get games working w/ wine, my Xserver no longer works. If I change the driver back to "nv" it works fine, but whenever using "nvidia" it tanks. Any ideas?? Thanks

edit: The output from the X says that it can't load the nVidia GLX module, whenever i look at my xorg.conf under module it has # Load "GLcore" and Load "glx" Would I have to change something in there??

---

### Post by moeFinley on 2007-01-10
How about re-installing it with something like [Automatix]("http://www.getautomatix.com/")?

If it's a problem with your xorg.conf file you can run ```
nvidia-xconfig
``` and it will try and correct any problems.  Delete the contents of your xorg.conf file and it will write it from scratch.

---

### Post by MeathooK427 on 2007-01-10
Automatix installs a quite outdated nvidia driver, unless they just updated..

---

### Post by moeFinley on 2007-01-10
Automatix installs the latest stable version.  If you want the beta there are installation instructions [here]("http://albertomilone.com/driver.html")

---

### Post by bodhi.zazen on 2007-01-10
Envy is also very east:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From CLI:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

---

### Post by MeathooK427 on 2007-01-10
Resolved: Reinstalled driver w/ this link: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2)

---

