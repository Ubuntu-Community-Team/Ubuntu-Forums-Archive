---
title: "Kubuntu just replaced my xorg.conf monitor section with this"
date: 2006-11-01
forum: General Help
---

### Post by ehird on 2006-11-01
```

Section "Monitor"
  identifier "Compaq V70"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Compaq V70 Display"
  Device "SiS Mirage"
  Monitor "Compaq V70"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

```

WHY?!!! I've lost all my resolution info and everything!!!!!!](*,) ](*,) ](*,) ](*,)

---

### Post by regeya on 2006-11-01
> WHY?!!! I've lost all my resolution info and everything!!!!!!](*,) ](*,) ](*,) ](*,)

Look in the /etc/X11; if you'd edited your xorg.conf before, it should have saved a backup.  I restored my settings from backup.

I truly hope this is a one-time thing; if I'm going to get my xorg.conf nuked on boot, I'm not an Ubuntu user anymore.  Automagic settings whether I want them or not are a real deal-breaker for me.

---

