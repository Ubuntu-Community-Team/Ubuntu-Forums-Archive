---
title: "Volume control not working!"
date: 2007-08-21
forum: General Help
---

### Post by fjf on 2007-08-21
I have searched but no help found.  I have only one sound device, and external USB soundcard, and USB-sound is set as the 0 device in my /etc/modprobe.d/alsa-base file.  I get sound, music, everything.  However, the gnome panel master volume control only shows one channel to control, PCM.  It is selected, but the master volume control can go up or down, or even be muted with no effect on the sound.  Any ideas?.

---

### Post by jnorthr on 2007-08-21
you know the panel that shows the PCM option ? I think there are several other choices that are hidden there and you should be able to turn them on. Check the man pages.

---

### Post by fjf on 2007-08-21
I see nothing there.  Sorry!.

---

### Post by forestpixie on 2007-08-21
if you right click the volume icon and open volume control you only have 1 PCM control and no more in edit preferences?

what about if you open a terminal and run 

```
alsamixer
```

---

### Post by mcduck on 2007-08-21
Go to System/Preferences/Sound and in the bottom of the Devices-tab there's section called 'Default Mixer Tracks'. Set there the sound card you want to use and select the tracks you want to control with your volume keys (you can select multiple tracks using Ctrl).

---

### Post by fjf on 2007-08-21
Same thing.  In alsa mixer only one channel, PCM, and If I go up or down in volume with the arrows in the keyboard nothing happens.

---

### Post by fjf on 2007-08-21
> **mcduck said:**
> Go to System/Preferences/Sound and in the bottom of the Devices-tab there's section called 'Default Mixer Tracks'. Set there the sound card you want to use and select the tracks you want to control with your volume keys (you can select multiple tracks using Ctrl).

There is one sound card only ,  USB audio codec (Alsa mixer), and only one device, PCM, selected.

---

### Post by forestpixie on 2007-08-21
what sort of sound card is it - have you looked anywhere else for help

---

### Post by fjf on 2007-08-21
It is an Aqvox dac.  But this is not the question; the problem is why the usb-sound volume cannot be changed from the main panel.  I can use the application's volume (i.e. amarok volume control), but not the main volume control in gnome.

---

### Post by forestpixie on 2007-08-21
no indeed you're right - just trying to get more info - as it is I can't help :(

---

### Post by forestpixie on 2007-08-22
what output do you get in terminal when running this

```
amixer scontrols
```

---

### Post by fjf on 2007-08-22
I get:  "Simple mixer control 'PCM',0"

---

### Post by forestpixie on 2007-08-22
all i could suggest would be contacting aqvox - it does show it as compatible with linux on the site, but I'm sure you know that  - but 1 control certainly seems odd? you'd get more than that with a 20 year old  card!

---

### Post by fjf on 2007-08-22
Thanks for trying!.

---

