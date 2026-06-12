---
title: "FLUXBUNTU-Logon/Logoff without password"
date: 2008-01-19
forum: General Help
---

### Post by BrendaninBrazil on 2008-01-19
I have installed Fluxbuntu on an old PC for my mother-in-law. Need it as simple as I can get it & am hoping to be able remove the need for a username & password to logon & password to logoff. I know Ubuntu has an option to disable this, is there a way to the same for Fluxbuntu?

Also, does anyone know how to automatically enable num lock at startup?

Please respond in really simple terms if possible as I am really new at this.:confused:

Thanks,

---

### Post by aysiu on 2008-01-20
Try this:
[HowTo: Create a Passwordless / Guest Login (Simple Method)](http://ubuntuforums.org/showthread.php?t=513820)

Since it changes the /etc/shadow file and doesn't rely on GDM or Gnome, I think it should work for Fluxbuntu as well.

---

### Post by BrendaninBrazil on 2008-01-20
Thanks very much Aysiu - it works as described. It looks like this is the best I can get it for the moment. I hope they add the option to bypass the logon screen altogether for Fluxbuntu the same as you can in Ubuntu.

---

### Post by aysiu on 2008-01-20
> **BrendaninBrazil said:**
> Thanks very much Aysiu - it works as described. It looks like this is the best I can get it for the moment. I hope they add the option to bypass the logon screen altogether for Fluxbuntu the same as you can in Ubuntu.
Well, if you install GDM in Fluxbuntu, you can configure it to autologin, just as it does for Ubuntu: ```
sudo apt-get update
sudo apt-get install gdm
gksudo gdmsetup
```

---

