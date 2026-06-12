---
title: "Customising the Desktop Environment in Precice"
date: 2012-10-29
forum: General Help
---

### Post by oxf on 2012-10-29
Is there a easy way to customise the the GNOME desktop in precise? It seems to me that  in previous releases had more options than Precise does.

E.G   in Maverick which I still have on my other PC I could go to System>Preferences>Appearance and change the themes/borders etc. Now the options are very limited. There was a simple way to move the buttons to the right side. I can't do that anymore! 

?Can you import more themes into System>....Appearance in Precise??

I have installed the Ubuntu Tweak Tool but even that dosen't give many theme options and certainly doesnt allow you to shift the buttons to the right (correct me if I'm wrong)

Thanks
Veronica

---

### Post by Frogs Hair on 2012-10-29
Install the Gnome Tweak Tool which includes theme,font and other settings.Once installed you can install Gnome 3.4 Themes from the link.  [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=0eee31b0f30be8d318c64d5847ebaff4](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=0eee31b0f30be8d318c64d5847ebaff4)

If you are interested in tweaking software and additional lenses for Unity and so on you can look here. [http://www.webupd8.org/](http://www.webupd8.org/)

---

### Post by jerrrys on 2012-10-29
Have you seen this?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by oxf on 2012-10-30
> **Frogs Hair said:**
> Install the Gnome Tweak Tool which includes theme,font and other settings.Once installed you can install Gnome 3.4 Themes from the link.  [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=0eee31b0f30be8d318c64d5847ebaff4](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=0eee31b0f30be8d318c64d5847ebaff4)

If you are interested in tweaking software and additional lenses for Unity and so on you can look here. [http://www.webupd8.org/](http://www.webupd8.org/)

Thanks. Yes I installed Gnome Tweak, the only thing is while useful it only allows you to tweak certain things and theres no way of importing additional themes into it.

@jerrys
Thats useful thanks!

I guess overall I'm a bit dissapointed with Precise. Sure it runs nice enough but with Gnome DE at least a lot of things are gone and can only be adjusted with more compex tweaks or commands. With previous GNOME2 everything could be customised from the appearance menu including colours, thems etc. Maybe I should have given Unity more of a chance? I'll play with it but suspect eventually I might have to try something like Mint.

Veronica

---

### Post by COMECON on 2012-10-30
You could also try **MyUnity**. It's available from the Software Center, and it allows you to enable/disable window animations, add a "desktop button" on the dash, change the theme, and lots of more stuff.
Another option is installing **CompizConfig Settings Manager** (also available from the SC) which allows you to change lots of things of the GNOME 3 desktop and the Unity plugin.
And, finally, you also have the **dconf** editor, which is a bit like Windows' regedit, you can change in example the location of the window buttons.

Greetings,
*~comecon*

---

### Post by oxf on 2012-10-30
> **COMECON said:**
> You could also try **MyUnity**. It's available from the Software Center, and it allows you to enable/disable window animations, add a "desktop button" on the dash, change the theme, and lots of more stuff.
Another option is installing **CompizConfig Settings Manager** (also available from the SC) which allows you to change lots of things of the GNOME 3 desktop and the Unity plugin.
And, finally, you also have the **dconf** editor, which is a bit like Windows' regedit, you can change in example the location of the window buttons.

Greetings,
*~comecon*

Thanks :)

---

### Post by Frogs Hair on 2012-10-30
Themes can be installed in .themes in home hidden folders but you need to crate the folder . Usr/share/themes is another location which will make them available to all users. 

Here are two applications I am currently using but the second is like MyUnity which is not available in 12.10 yet.
   
[http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)


[http://www.webupd8.org/2012/10/tweak-unity-with-unsettings-008-now.html](http://www.webupd8.org/2012/10/tweak-unity-with-unsettings-008-now.html)

---

### Post by deadflowr on 2012-10-30
If you're running gnome-shell, here:

[https://extensions.gnome.org/]("https://extensions.gnome.org/")

---

### Post by oxf on 2012-10-30
> **Frogs Hair said:**
> Themes can be installed in .themes in home hidden folders but you need to crate the folder . Usr/share/themes is another location which will make them available to all users. 

Here are two applications I am currently using but the second is like MyUnity which is not available in 12.10 yet.
   
[http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)


[http://www.webupd8.org/2012/10/tweak-unity-with-unsettings-008-now.html](http://www.webupd8.org/2012/10/tweak-unity-with-unsettings-008-now.html)

Hmm OK then. But that raises another question.
If I go to usr/share/themes theres a whole bunch of themes.
However, they dont all show up in GNOME Tweak Tool. And even less in System Tools>Settings>Appearance.

---

### Post by Frogs Hair on 2012-10-30
Many of them are window borders that are installed by default. When you install downloaded themes make sure they are fully extracted and you are using the correct version. 11.10 uses GTK 3.2, 12.04 uses 3.4,and 12.10 uses 3.6. themes. Appearance settings will only display official themes such as Ambiance, Radiance, Adwaita, and Accessibility themes.

---

### Post by oxf on 2012-10-31
> **Frogs Hair said:**
> Many of them are window borders that are installed by default. When you install downloaded themes make sure they are fully extracted and you are using the correct version. 11.10 uses GTK 3.2, 12.04 uses 3.4,and 12.10 uses 3.6. themes. Appearance settings will only display official themes such as Ambiance, Radiance, Adwaita, and Accessibility themes.

Thanks for all the hints. I'll figure it out eventually!

Veronica

---

