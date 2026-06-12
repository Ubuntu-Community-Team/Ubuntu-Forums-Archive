---
title: "GTK Theme Ignores Some Applications"
date: 2008-06-21
forum: General Help
---

### Post by vintagecandy on 2008-06-21
I just installed the Darker GTK theme here: 
[http://www.gnome-look.org/content/show.php/Darker+theme?content=32768](http://www.gnome-look.org/content/show.php/Darker+theme?content=32768)
which looks fine on most applications, but it seems to ignore others, specifically Synaptic, the Login Window manager, Software Sources, and a few others under the "Administration" tab. Here's a screenshot showing the difference:
[IMG]http://i30.tinypic.com/v5lfua.png[/IMG] 
Any ideas about what may be causing this?

---

### Post by ad_267 on 2008-06-21
Edit: Ignore that, I tried it on mine and it works for me. What version of Ubuntu are you using? There are usually differences because when you run synaptic you are running as the root user who has different settings, but I think Ubuntu usually takes account of this. The only difference for me is my icon theme isn't the same.

---

### Post by vintagecandy on 2008-06-21
> **ad_267 said:**
> Edit: Ignore that, I tried it on mine and it works for me. What version of Ubuntu are you using? There are usually differences because when you run synaptic you are running as the root user who has different settings, but I think Ubuntu usually takes account of this. The only difference for me is my icon theme isn't the same.

I'm using Hardy.  I don't have this problem with other GTK themes so I figured it was something specific to this theme.

---

### Post by ad_267 on 2008-06-21
OK I think the problem is the particular theme isn't installed in the root folder. Ubuntu seems to check when you open synaptic etc whether the theme you have is available for root and then apply it and your settings.

Run this and then reapply the theme.
```
sudo cp -R /home/your_username/.themes /root/.themes
sudo cp -R /home/your_username/.icons /root/.icons
```

---

### Post by vintagecandy on 2008-06-21
That did it!  Thanks!

---

### Post by Occasionally Correct on 2008-06-21
You may want to use ln -s instead of cp -R:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

Instead of just copying the files to your /root directory, it'll link them so that it'll withstand future theme changes. (This also works for your fonts if you want to link ~/.fonts and ~/.fontconfig.) :)

---

### Post by ad_267 on 2008-06-21
> **Occasionally Correct said:**
> You may want to use ln -s instead of cp -R:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

Instead of just copying the files to your /root/ folder, it'll link them so that it'll withstand future theme changes. (This also works for your fonts.) :)

Yeah that's a better idea. Doh! Why didn't I think of that haha. Do a
```
sudo rm -rf /root/.icons
sudo rm -rf /root/.themes
``` first then do that.

---

