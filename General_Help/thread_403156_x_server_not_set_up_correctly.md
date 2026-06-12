---
title: "x server not set up correctly"
date: 2007-04-06
forum: General Help
---

### Post by Dragon665 on 2007-04-06
Im not really getting anwhere here, I have other posts in Absolute beginner and Installation & Upgrades and i dont seem to be getting many replies if any at all. Basically after installing Ubuntu off the alternative text based version and taking the disc out to start it up i get this error: "Failed to start X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?" I press yes and scroll to the bottom to see: - "Fatal server error: no screen found"
Now i have an Nvidia 8800 gts 640 mb graphics card and have tried the 'sudo dpkg-reconfigure xserver-org' and went through all that and still got the same error.

Any help would be nice.

Roy

---

### Post by Dragon665 on 2007-04-06
grrrrr
how do i complain

---

### Post by ajgreeny on 2007-04-06
If you're using an nvidia driver at the moment, try using vesa instead when you do the 'sudo dpkg-reconfigure xserver-xorg' (I think you made a typo in your command in this post).  At least that should get you a gui and you can then try to work out the problem from there. It is probably a driver issue that is causing the problem, but I can't help any more than that, I'm afraid.

---

### Post by Tanker Bob on 2007-04-13
I just installed an 8800GTS and have the same issue.  The VESA driver installed by default on mine and gives me a graphical interface at 56Hz--it flashes the screen badly.  I tried changing the driver to the open source NVidia one, but Kubuntu changes it back to VESA when restarting the X server.  Any other attempt to fix it results in a text-only interface.

I will tackle this head-on this weekend and update my progress here.  I plan to use Envy 0.9.1 to install the proprietary driver.   If that fails, I'll try installing the NVidia driver manually.

---

### Post by Tanker Bob on 2007-04-13
Well, that didn't take long.  I uninstalled the old NVidia drivers and then installed Envy 0.9.1 from the text shell.  I executed Envy in text mode, told it to uninstall the drivers (just for insurance) and then told it to install the NVidia drivers.  The installation and its included recompiles went fine, but that just got me started.

The install worked in that the NVidia setup recognized the 8800GTS, but it only displayed at 59 Hz.  While it didn't flicker, I prefer 72 Hz for good video stability.  I also wasn't happy with the NVidia Settings limitations at this stage.  Neither xorg.conf nor NVidia Settings seemed to recognize my monitor, so it limited its vertical scan rate to 60 Hz.  So, I went into an older xorg.conf backup and copied out the old lines for the monitor then pasted them into the new xorg.conf.  I also added the resolutions that I wanted into the new xorg.conf.  This didn't work at first, returning to the text mode after trying to restart the X server.  I ran nvidia-config several times, receiving an error each time that the default monitor could not be found in the file.  After these attempts, I ran out of ideas and decided to reboot.

After rebooting the system, everything worked fine.  I was able to go into NVidia Settings and set the vertical refresh to 72 Hz.  All is stable and fully operational.  The Envy script did its job as advertised, but NVidia's configuration software didn't work as well as possible.  OTOH, Vista doesn't support the 8800GTS or GTX very well, either.

I hope that this helps someone.

---

