---
title: "Nvida-glx drivers on Gutsy"
date: 2007-10-18
forum: General Help
---

### Post by meimato on 2007-10-18
I've upgraded from Feisty to Gutsy and now my previously working ndivia accelerated drivers work no more. If I enable "accelerated nvidia drivers" from the Restricted driver manager and reboot my computer, X only starts in low resolution mode, using the vesa drivers at 800x600 resolution; If I look in my dmesg I find this two lines:

nvidia: module license 'NVIDIA' taints kernel
NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007

If I use the nv drivers I have no problems running at full 1280x1024 resolution, but obviously no destkop effects can be enabled...

My card is an Asus EN7900GS (which worked flawlessy on Feisty, as I said)

---

### Post by r-mo on 2007-10-18
go into synaptic and make sure you have nvidia-glx-new installed rather than nvidia-glx.  If it is try running sudo dpkg-reconfigure xserver-xorg -phigh  as screens and resolutions can be pretty flaky

---

### Post by Zeikcied on 2007-10-18
I hope you don't mind me using your thread, but I've had similar trouble with the nvidia-glx drivers.

I'm using Kubuntu, and in the System Settings there is a section for Restricted Drivers.  I used that menu to enable the NVIDIA drivers for my 7600GS.  When I rebooted, nvidia-settings didn't detect my monitor properly, and said the max setting was 640x480.  Even though my monitor goes beyond 1280x1024 (its preferred resolution).  So I spent a lot of time in a text environment (the original setting was too low for my monitor to even display), and some more time in KDE (once I got to that point).

I don't know if it was the nvidia-glx-new package or not, but I would assume it was.  But I eventually disabled the driver, which uninstalled it.  And now I'm back with the default nv drivers.

---

### Post by chrisccoulson on 2007-10-18
I had a similar problem as well after upgrading from Feisty. I couldn't get the NVIDIA drivers to work. After installing nvidia-glx-new, I was always presented with failsafe-X session. For some reason, it started working after I purged and reinstalled nvidia-glx-new and the linux-restricted-modules packages.

BTW, my NVIDIA drivers had been installed via Envy on Feisty. Not sure whether this had anything to do with my problem.

---

### Post by Pumalite on 2007-10-18
I think the 'linux-restricted-modules' package did the trick.

---

### Post by meimato on 2007-10-18
No way.
I checked and had the nvidia-glx-new installed.
If I do sudo dpkg-reconfigure xserver-xorg -phigh it only sets nv drivers in my xorg.conf, so disabling nvidia ones.

---

### Post by flyboy284 on 2007-10-19
I'm having trouble installing the drivers. the nvidia-glx drivers are not in the repository.
When trying the Restricted Drivers Manager it just says nvidia-glx is not enabled.
Envy won't work either.

---

### Post by meimato on 2007-10-19
I managed to enable nvidia drivers using envy (but it's a shame ubuntu toold didn't work).
Now, when I enable Desktop Effects, all windows loose borders: title bar, status bar...

---

### Post by Nunu on 2007-10-19
There might be issues with downloading packages from the repositories due to the massive demand on servers.

I had similar issues with Feisty when i installed the visuals add on beta. as soon as i enabled them the Nvidia config went kaboom (Technical Term)

---

### Post by useResa on 2007-10-19
> **meimato said:**
> I managed to enable nvidia drivers using envy (but it's a shame ubuntu toold didn't work).I fully agree with you here, I have tried installing both nvidia-glx or nvidia-glx-new in various ways.

Tried synaptics, tried the restricted driver manager, tried the CLI and module-assistant. Downloaded the latest driver from nVidia site and installed that. All I got was the "low graphics" mode and only high resolution when using the nv driver.

Envy installed the nVidia driver nicely (noticed btw it was the latest release from the nVidia site) and has given me my high resolution back again. 
Don't know what tselliot does extra or what I might have forgotten, but sure am glad that I have it up and running again.
If we could only achieve the same ....

---

### Post by Nunu on 2007-10-19
> **useResa said:**
> I fully agree with you here, I have tried installing both nvidia-glx or nvidia-glx-new in various ways.

Tried synaptics, tried the restricted driver manager, tried the CLI and module-assistant. Downloaded the latest driver from nVidia site and installed that. All I got was the "low graphics" mode and only high resolution when using the nv driver.

Envy installed the nVidia driver nicely (noticed btw it was the latest release from the nVidia site) and has given me my high resolution back again. 
Don't know what tselliot does extra or what I might have forgotten, but sure am glad that I have it up and running again.
If we could only achieve the same ....

Do you buy any chance know if the new driver enables multi head displays out the box or if you need to go hack the XORG file again as with Feisty?

---

### Post by useResa on 2007-10-19
> **Nunu said:**
> Do you by any chance know if the new driver enables multi head displays out the box or if you need to go hack the XORG file again as with Feisty?Sorry ... don't know.
My guess ... hack the xorg file ... but AFAIK you can save a copy of your xorg and re-use it once you have installed the new driver.

---

### Post by Spr0k3t on 2007-10-19
> **Nunu said:**
> Do you buy any chance know if the new driver enables multi head displays out the box or if you need to go hack the XORG file again as with Feisty?

You have to `gksu nvidia-settings' to configure multiple display.  Make sure you have the correct restricted driver for your card though.

---

