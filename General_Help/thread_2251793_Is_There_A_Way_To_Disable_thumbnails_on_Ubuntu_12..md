---
title: "Is There A Way To Disable thumbnails on Ubuntu 12.04?"
date: 2014-11-06
forum: General Help
---

### Post by jooge on 2014-11-06
Is there a way to disable thumbnails from being made (captured) on Ubuntu 12.04? I'm referring in:

~/home/xxxx/.thumbnails

Thanks in advance.

---

### Post by ringstaart on 2014-11-06
You could try emptying the .thumbnails directory, and then running

```
chmod -w /home/xxxx/.thumbnails
```

This should make the directory read-only, meaning that it can't be changed.

Don't put the tilde (~) in front of "/home/", by the way. ~ stands for "/home/yourname/", so "~/home/xxxx/.thumbnails" stands for "/home/xxxx/home/xxxx/.thumbnails".

---

### Post by coldcritter64 on 2014-11-06
Any nautilus window > Edit > Preferences > Preview tab --> Then change the settings for "Text files" to "Never" and "Other previewable files" to "Never". Check your icons, they should now all be the default blank ones, no thumbnails should now show up. Cheers.

---

### Post by Bucky Ball on 2014-11-07
> **coldcritter64 said:**
> Any nautilus window > Edit > Preferences > Preview tab --> Then change the settings for "Text files" to "Never" and "Other previewable files" to "Never". Check your icons, they should now all be the default blank ones, no thumbnails should now show up. Cheers.

^^^
This. ;)

---

### Post by ringstaart on 2014-11-07
> **coldcritter64 said:**
> Any nautilus window > Edit > Preferences > Preview tab --> Then change the settings for "Text files" to "Never" and "Other previewable files" to "Never". Check your icons, they should now all be the default blank ones, no thumbnails should now show up. Cheers.

It sounds like he doesn't want thumbnails to be made at all. Does this stop them from being made, or does it only stop them from showing up in Nautilus?

---

### Post by coldcritter64 on 2014-11-07
If the OP runs a standard install then the folder remains empty.  But to answer your question, if another browser were used, like thunar, YES the folder will be used.

In that case the following command will also disable any other thumbnailers under gnome settings, set either with dconf-editor (org.gnome.desktop.thumbnailers disable-all) or the following terminal command.

```
gsettings set org.gnome.desktop.thumbnailers disable-all 'true'
```

In which case this as well should ensure NO thumbnails under any use case, even if a browser like thunar for example was used.

I prefer to use settings where possible. Though, as a final resort, I wouldn't hesitate to use the permissions suggestion. In this case I don't think it will be needed. I am glad you pointed it out as I tend to assume standard installs unless otherwise stated, and the gnome setting takes care of that use case (another browser etc using the gnome thumbnail settings). Cheers.

**EDIT:** seems I may be wrong about the gnome settings when thunar is used wrt thumbnails, it is still using the folder here (though I do have a seriously custom install running here so am unsure if it is just my set up)
[B]
@ OP,[/B] keep a close check on the thumbnails folder for a bit and see if settings are sufficient, _*then try the folder permissions if not*_. The gnome settings should cover thumbnails despite my cantankerous install, but on further testing my advice seems to be failing for some reason.
[B]
Edit 2:[/B] @ OP, if you do use any other application that generates thumbnails, don't just rely on that gnome setting, go into Edit > Preferences for each app and detick any "show thumbnail" settings that are set. I just found a similar setting in thunar that was causing the above hassle.
My custom install has both gnome and xfce DEs side by side with both xfdesktop and nautilus desktop running at the same time, toggled with an xfce panel launcher pointed at a custom script containing 2 wmctrl commands. Hence I suspect this setup allowed the xfce settings helper to play up with the gnome settings being ignored.

---

### Post by jooge on 2014-11-07
Awesome help everyone. You gave me just what I was looking for.

> **ringstaart said:**
> 
Don't put the tilde (~) in front of "/home/", by the way. ~ stands for  "/home/yourname/", so "~/home/xxxx/.thumbnails" stands for  "/home/xxxx/home/xxxx/.thumbnails".

I see that now. My bad. Thanks for the tip.

---

