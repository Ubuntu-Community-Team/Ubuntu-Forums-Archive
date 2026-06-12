---
title: "VRAM Not Detected Correctly At All"
date: 2007-08-06
forum: General Help
---

### Post by Vince4Amy on 2007-08-06
Hello.

The card I'm using is an ATI Radeon 9550, 256Mb Video Memory.

I'm using the restricted-manager ATI Driver. I've just discovered that Ubuntu seems to be detecting my video memory as 128Mb, which obviously is wrong. My attempts of installing the latest driver failed so I reverted. So what is happening to the missing VRAM?

---

### Post by dreadlord_chris on 2007-08-06
hmmm.... I had to actually tell Ubu how much VRAM I had - it never detected it by its self...
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf

```
add this to the **Device** section:
```

VideoRam ####

```
replace #### with the amount of VRAM you have *in kilobyts*, save the file, restart X.

---

