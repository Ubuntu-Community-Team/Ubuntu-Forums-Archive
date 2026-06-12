---
title: "nvidia-settings and external monitor issues"
date: 2014-03-18
forum: General Help
---

### Post by bogren on 2014-03-18
I'm having some issues with the nvidia-settings. After much T&E it finally looks like I have managed to install nvidia-331 driver along with bumblebee (using this guide: [http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271](http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271)) without the black screen on boot. But nvidia-settings isnt working properly, it only shows two of the categorys:

"Application Profiles" and "nvidia-settings configuration". No screens and other options. when I run it from terminal I get this error message 

```
$ nvidia-settings

** (nvidia-settings:4909): WARNING **: PRIME: Failed to execute child process "/usr/bin/prime-supported" (No such file or directory)
** Message: PRIME: is it supported? no


```

Also, it seems like the nvidia-xconfig isn't installed along with the driver (nvidia-xconfig: command not found). Is that no longer included with the 331.x ver fo the driver for some reason? this is a dump with installed packages filtered for nvidia. [https://www.dropbox.com/s/s7y27ffgab0tt6s/synaptic.png](https://www.dropbox.com/s/s7y27ffgab0tt6s/synaptic.png)

The support for dual monitors is also gone ( before installing nvidia driver I could use the external monitor but it was not funktioning properly and was freezing and the display settings would not respond after trying to change the settings like arrangement etc.) I googled it a bit and found this guide: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup). I am just about to try it but if you know how to get my ecternal monitor to work, I would appreciate your input!

If anyone could give me some help on this things I would be most appreciative. Let me know if you need some more info.
I'm on a Asus Zenbook with a nvidia GT 650M card (with optimus).

After all this hastle though, I have to quote Linus Thorvald: Nvidia, F*CK YOU!!

---

### Post by buminda on 2014-05-09
Hello , I'm having the same issue . NVIDIA x server settings doesnt show up the Xserver settings and X Server Display configurations. Can somebody help me . I'm using ubuntu 12.04 LTS and , with my lenovo laptop brightness adjustment is not working.

---

### Post by MartyBuntu on 2014-05-09
> **bogren said:**
> 
After all this hastle though, I have to quote Linus Thorvald: Nvidia, F*CK YOU!!

He actually (more or less) took that back.

Try and keep up.

---

