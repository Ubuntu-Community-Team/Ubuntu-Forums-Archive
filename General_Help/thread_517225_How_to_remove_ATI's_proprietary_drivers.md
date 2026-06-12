---
title: "How to remove ATI's proprietary drivers?"
date: 2007-08-04
forum: General Help
---

### Post by CroEragon on 2007-08-04
Well, i think title speaks for itself!!!

How to remove ATI's proprietary drivers?

I have a reason to believe that ATI's drivers cause problems even now when i switched to nVidia's card and using "nv" drivers.

---

### Post by CroEragon on 2007-08-04
Bump!

I really need help with this!

---

### Post by apetresc on 2007-08-04
All you have to do to completely get rid of the files related to those drivers is ```
sudo apt-get remove fglrx
```
However, if your xorg.conf file is set to use 'nv' instead of those drivers, there is **no way** for them to cause crashes in X. Maybe in Windows, uninstalled programs reach over from across the grave to cause problems, but Ubuntu puts those spirits to rest properly :)

---

### Post by CroEragon on 2007-08-04
I want to believe same but listen to this.

When i first installed ubuntu, my onboard graphic card (ATI Radeon XPRESS 200) worked perfectly well with Open Source driver, only problem was lack of 3D Acceleration. When i fell in love with beryl and looking glass i decided to instal ati's drivers to enable it. I did enable 3D Acceleration, but then my computer started to freeze on periods of 10-15mins. I did extensive research and tests ( tried ati's drivers on openSUSE and Mandriva for same effect, enabling 3d and freezing problem) and i concluded that problem must be in drivers. Now when i got  nVidia card (nVidia GeForce 7600 GS)  and using open source "nv" drivers, im still experiencing same problem. Only logical explanation is that fglrx changed some parameters in system, triggering bug. My understanding of installation process  in Ubuntu is that uninstalling will revert all changes made by that drivers.

Am i right?

Thats why i wanna remove them.

Thanks for response.

---

### Post by CroEragon on 2007-08-04
When i put in commant you said i get ```
sudo apt-get remove fglrx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fglrx

```

I'm 100% sure i installed it and sure i didn't remove it before, hence, i didn't know how.

---

### Post by apetresc on 2007-08-04
Oops, my bad! The correct package name is "xorg-driver-fglrx"

Also you may want to check out [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") which will take care of managing ATI/NVidia drivers for you.

---

### Post by CroEragon on 2007-08-04
Thank you for your help.

Wierd enough, it seams like it worked. I removed it and restarted computer, now im updating my Ubuntu almost an hour, no freezing, before i couldn't manage more than 10mins before it freezes.

Ill test it bit more, than install nVidia drivers, and check out that Compiz Fusion thing, seems like my beryl is discontinued, gotta switch.

---

