---
title: "I can't change LightDM wallpaper and user image"
date: 2017-08-31
forum: General Help
---

### Post by chief096 on 2017-08-31
Hi! I've an issue regarding LightDM on my Lubuntu OS. Substantially I can't change my background image (which is always black) and profile image, also this one ever the same. I've tried to change them with lubuntu's default tool LightDM GTK+ Greeter Settings, but the wallpaper remains still black and profile image still the same. I've tried also to check my /etc/lightdm/lightdm-gtk-greeter.conf and I see nothing wrong. Which may be the cause?

---

### Post by again? on 2017-08-31
Can you change other settings like theme/icons or window position?
Do you use disk encryption?
Do you have another greeter installed?
```
apt list --installed *greeter
```

---

### Post by chief096 on 2017-09-02
I can change the theme or window position, but not profile image or wallpaper. Also giving ```
apt list --installed *greeter
``` it returns to me as result: **lightdm-gtk-greeter/zesty,now 2.0.1-2ubuntu4 i386 [installed]**. So I've only LightDM greeter installed

---

### Post by again? on 2017-09-02
Try setting a background from /usr/share/backgrounds
May be a permission issue which is why I asked about encryption.

I can use any image for my profile (svg,jpg or png) as long as all users can read the file.
Images aren't resized so you don't want to use much larger than 96x96 px.

---

### Post by chief096 on 2017-09-03
Ok thanks, now it works. Checking image's permissions I noticed that "view content" was set only for owner and not for anyone. Now also works the changing of profile image, but I don't really know the reason :P. However now I sign topic as solved and thanks again.

---

