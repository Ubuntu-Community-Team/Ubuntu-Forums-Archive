---
title: "No sound output"
date: 2017-05-07
forum: General Help
---

### Post by mr-mister on 2017-05-07
Hi everybody! I had been having some issues with audio recentley, it wood randomly not recognize devices and mic didn't work very well. I have a Hp-14ac129la with ubuntu 16.10 and windows 10. Windows didn't show the same audio problems.  Suspecting a driver issue i followed these instructions [http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/#comment-4303](http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/#comment-4303) . Both make and sudo make install gave me a dependency error, so i ran sudo aplay -l and no devices were found. Then i tried installing the sound modules that apparently were missing with sudo apt-get install linux-restricted-modules-'uname -r' linux-generic but returned 
E: Unable to locate package linux-restricted-modules-4.8.0-49-generic
E: Couldn't find any package by glob 'linux-restricted-modules-4.8.0-49-generic'
E: Couldn't find any package by regex 'linux-restricted-modules-4.8.0-49-generic'
After that i restarted computer and no sound came out (default desktop background was back on for some reason, but that may be because i was checking if i could solve something configuring bios and i corrected system time that was a couple of hours ahead)
  Sound output now shows that it's playing through 'dummy output'.
any ideas?

---

### Post by Yellow Pasque on 2017-05-07
> **mr-mister said:**
> Suspecting a driver issue i followed these instructions [http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/#comment-4303](http://airbornesurfer.com/2015/04/how-to-install-realtek-hd-audio-driver-in-linux/#comment-4303) . 

Bad idea. The driver you need is already built into the kernel. There's no need to download a driver from manufacturer (this isn't Windows). Besides, Realtek hasn't updated their own version of the Linux sound driver in years and it won't build on modern kernels, as you've discovered.

> Then i tried installing the sound modules that apparently were missing with sudo apt-get install linux-restricted-modules-'uname -r' linux-generic

I don't think l-r-m has been used since 2.x kernel days. You seem to be following outdated advice.

> Sound output now shows that it's playing through 'dummy output'. any ideas?

Was it showing dummy output before you tried the Realtek driver? I would run 'sudo make uninstall' from the directory where you tried to build the Realtek driver. Then ,I would reinstall the kernel image package to restore files that got overwritten/removed.
```
sudo apt-get install --reinstall linux-image-`uname -r`
```
Reboot. Get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mr-mister on 2017-05-07
It didn't show dummy output before, it would simply show as if there were no devices available and no sound came out. I'm really new with handling these situations so it doesn't surprise me to have taken a wrong turn on this. But i really appreciate the help.
Your suggestion did not work, nonetheless, here is the actual state of the situation [http://www.alsa-project.org/db/?f=a4a0170807cfee1764465763cd3273378bf0c224](http://www.alsa-project.org/db/?f=a4a0170807cfee1764465763cd3273378bf0c224)

---

### Post by Yellow Pasque on 2017-05-07
```
!!ALSA Version
!!------------

Driver version:     
Library version:    1.1.2
Utilities version:  1.1.2
```

Something is wrong with the kernel sound driver(s)/module(s). It see it happen all the time after folks try and install the Realtek driver. I'm not sure how to fix it.
Try loading the module manually and see output:
```
sudo modprobe -v snd-hda-intel
```

---

### Post by mr-mister on 2017-05-07
Output: 
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/b43.conf line 4: ignoring bad line starting with 'exit'
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/b43.conf line 6: ignoring bad line starting with 'exit'
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/b43.conf line 7: ignoring bad line starting with 'q'
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/b43.conf line 8: ignoring bad line starting with 'quit'
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/b43.conf line 9: ignoring bad line starting with 'done'
modprobe: FATAL: Module snd-hda-intel not found in directory /lib/modules/4.8.0-49-generic

As a matter of fact the b43.conf content is:
exit

exit
q
quit
done

and i found the snd-hda-intel.ko in /lib/modules/4.8.0-41-generic/kernel/sound/pci/hda/
Perhaps something to do with that

---

### Post by Yellow Pasque on 2017-05-07
> FATAL: Module snd-hda-intel not found in directory /lib/modules/4.8.0-49-generic 

My fault. I think you also needed to reinstall image-extra:
```
sudo apt-get install --reinstall linux-image-extra-`uname -r`
```

---

### Post by mr-mister on 2017-05-07
it worked! Mic still records strange and i'll have to see if it doesn't catch devices again. It also happens when i plug in hdmi while i'm seeing a movie or something. 
One step at a time, Thanks!

---

