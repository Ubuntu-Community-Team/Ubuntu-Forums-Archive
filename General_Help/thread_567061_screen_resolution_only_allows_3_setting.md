---
title: "screen resolution only allows 3 setting"
date: 2007-10-04
forum: General Help
---

### Post by trucker33377 on 2007-10-04
with this card i would think that there would be more settings how could i get a higher settings

---

### Post by PmDematagoda on 2007-10-04
Run nvidia-settings using:-
```

gksudo nvidia-settings
```

then go to Display configuration, change the resolution to what you want and then click the "Save to X configuration file", after that you can choose your new resolution.:)

---

### Post by trucker33377 on 2007-10-04
gksudo nvidia-settings still has the same 3 settings 1024x768 being the highest

---

### Post by elliotjreed on 2007-10-04
Try:

```
sudo dpkg-reconfigure xserver-xorg
```

Select your graphics card, then your resolution

If not:

[http://ubuntuforums.org/showthread.php?p=3306237]("http://ubuntuforums.org/showthread.php?p=3306237")

...and change values to your wanted res.

---

### Post by trucker33377 on 2007-10-04
i did that and went to link added higher 1280X1024 like it said saved it but there still is nothing past 1024X786. my refresh rate is at 60 that may need to be set higher but that looked kinda tough to get done

---

### Post by PmDematagoda on 2007-10-04
Ok, could you post your xorg.conf file? Get it using:-

```
sudo gedit  /etc/X11/xorg.conf
```

---

### Post by trucker33377 on 2007-10-05
well i must say i was about to give up on this. Nothing seemed to be going right with my new computer and linux. but one last shot was to try gutsy's new release, so thinking that maybe it being all new then just maybe it would work with my all new hardware. Boom install went very smooth booted right up. updated and rebooted just fine. ive got 2 HD's  one has windows and now feisty and gutsy share one 500 gig drive. I was very pleased to see the proper sreen resolution and even surprised to see that it asked me to install my new navida driver. ive only been working with linux just over a month and know very little about line commands so when i saw this WOW. a BIG hand goes out to all thos who worked on this project GUTSY GIBBINS great job!!

---

