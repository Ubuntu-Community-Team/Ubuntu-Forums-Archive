---
title: "Cannot reset Ubuntu splash to default."
date: 2017-10-01
forum: General Help
---

### Post by Hewjr100 on 2017-10-01
Installed Gnome in Ubuntu 17.04 Unity, then decided to remove after trying it out.  Removed using sudo apt remove --purge, but when I rebooted I still had the Ubuntu Gnome splash screen.  Tried installing plymouth alternatives and  and selected default  Ubuntu splash to no avail.  How can I reset splash to default.  The reason I removed Gnome is because in Unity I had trackpad off, but in Gnome it was also set to off, but trackpad was still working.  I have a habit of resting my wrist on my laptops trackpad.

Henry

---

### Post by Kirboosy on 2017-10-02
Hi Henry,

It appears your default splash screen has been changed to a new Plymouth theme. Please try running the following commands below and see if that fixes your issue.
[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]sudo update-alternatives --config default.plymouth[/FONT][/COLOR]
```[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]sudo update-initramfs -u[/FONT][/COLOR]
```[COLOR=#242729][FONT=Consolas]

Hope that helps!
~Caboose[/FONT][/COLOR]

---

### Post by Hewjr100 on 2017-10-02
Ok got it thanks.

Henry

---

