---
title: "Fuzzy font display"
date: 2021-11-07
forum: General Help
---

### Post by mbott on 2021-11-07
I've been away from Ubuntu for several years now, but I thought I'd check it out.  The install for 21.10 was extremely quick and flawless.  However, the font in the Ubuntu Software is extremely fuzzy.  Not sure where to go to review the display fonts.  Would appreciate a little guidance.

Here is what I'm seeing: [https://i.imgur.com/LpP4rlZ.png](https://i.imgur.com/LpP4rlZ.png)

Thanks!

-- 
Mike

---

### Post by QIII on 2021-11-07
Hello!

If you attempted to attach an image, none was attached.

---

### Post by mbott on 2021-11-07
> **QIII said:**
> Hello!

If you attempted to attach an image, none was attached.

Fixed

-- 
Mike

---

### Post by ActionParsnip on 2021-11-08
Does the system have a make and model?
If you are using an external display then check the cable is  seated correctly or try replacing it to test

---

### Post by mbott on 2021-11-08
> **ActionParsnip said:**
> Does the system have a make and model?
If you are using an external display then check the cable is  seated correctly or try replacing it to test

Thanks.  Had the opportunity to re-do the install and the font is now "normal".  :)  I guess the first install wasn't as good as I thought it was.

-- 
Mike

---

### Post by mbott on 2021-11-08
> **mbott said:**
> Thanks.  Had the opportunity to re-do the install and the font is now "normal".  :)  I guess the first install wasn't as good as I thought it was.

-- 
Mike

It was fine until I rebooted. then the font fuzzies returned.  The system is an ASUS i5-4672K CPU @ 3.40GHzwith 16GiB memory.  Graphics is the onboard Intel HD Graphics 4600 (HSW GT2).

-- 
Mike

---

### Post by Impavidus on 2021-11-08
Looks like font antialiasing is disabled. It must be somewhere in your settings (in Xubuntu, Settings&#8594;Appearance&#8594;Fonts&#8594;Enable font antialiasing, but in Ubuntu that may be different). You may have to restart the application or logout/login for the change to take effect.

---

### Post by philhughes on 2021-11-08
I have the same after an upgrade from 21.04. Some discussion here:

[https://forum.snapcraft.io/t/snap-store-font-issue-and-empty-looking/27379/2](https://forum.snapcraft.io/t/snap-store-font-issue-and-empty-looking/27379/2)

---

### Post by mbott on 2021-11-09
> **Impavidus said:**
> Looks like font antialiasing is disabled. It must be somewhere in your settings (in Xubuntu, Settings&#8594;Appearance&#8594;Fonts&#8594;Enable font antialiasing, but in Ubuntu that may be different). You may have to restart the application or logout/login for the change to take effect.
So far, I've been unable to locate any type of antialiasing setting anywhere.  UPDATE: Gnome Tweaks needed to be installed to add the antialiasing.  No help.  

-- 
Mike

---

### Post by mbott on 2021-11-10
This has been resolved for me.  I was originally installing 21.10 on an ASUS i5 desktop that I have.  It's pretty bare bones in that it just has the onboard video.  Installing on my ASUS laptop with the Geforce GTX 960M video and then switching to the 470 NVIDIA driver from the X.Org X server display driver has removed the "fuzzies".

-- 
Mike

---

