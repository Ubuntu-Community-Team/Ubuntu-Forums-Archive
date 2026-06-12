---
title: "Amd drivers installed but no panel and no launcher"
date: 2012-10-20
forum: General Help
---

### Post by elliotn on 2012-10-20
I just installed my ati drivers using the manual method but now I get a desktop with only a wallpaper no launcher and no panel.

unity --reset. 
gives me an error    the reset option is now deprecated

help please

---

### Post by elliotn on 2012-10-21
I guess I will have to do it myself

---

### Post by 3rdalbum on 2012-10-21
> **elliotn said:**
> I just installed my ati drivers using the manual method but now I get a desktop with only a wallpaper no launcher and no panel.

unity --reset. 
gives me an error    the reset option is now deprecated

help please

In future, don't use the manual method to install your graphics drivers.

"But I tried using the Additional Drivers program and it told me that there were no graphics drivers it could install!"

That's because the Radeon HD 2400 you're using is no longer supported by AMD's official driver. Sorry. You might have to remove it on the terminal and then probably remove the /etc/X11/xorg.conf file, also on the terminal, to get things back to normal.

---

### Post by 2F4U on 2012-10-21
The latest version of AMD proprietary drivers don't work with your card (if the information in your signature is correct), because ATI dropped support for older cards. You could install an older version of the driver, but this version would also require an older version of the Xorg stack.

[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

---

### Post by elliotn on 2012-10-21
> **2F4U said:**
> The latest version of AMD proprietary drivers don't work with your card (if the information in your signature is correct), because ATI dropped support for older cards. You could install an older version of the driver, but this version would also require an older version of the Xorg stack.

[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

I realised that my card isn't supported so I removed em.... solved

---

