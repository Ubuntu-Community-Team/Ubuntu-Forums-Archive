---
title: "Unity tweak tool. Themes and icons not changing"
date: 2017-06-12
forum: General Help
---

### Post by adamhff on 2017-06-12
Hello, so I have posted a message similar to this awhile back and got no replies to I decided to reword it. Basically my themes aren't getting applied in unity. I am trying desperately to use unity tweak tool to change my theme/icons and I have themes and icons installed correctly, but only some things are being changed. like the basic color scheme of the theme. The default ubuntu theme still shows through. The very top menu bar never changes colors or anything(still orange and black). The icons when I open it in 'files' are changed but not the launcher icons. I have tried unity tweak tool and gnome tweak tool, but no joy. I am wondering if there is a way of getting the theme into system settings > appearance > theme (like the actual official ubuntu theme manager, with radiance). I have tried restarting after applying the changes and reinstalling unity tweak tool. 

What could be going on here? 

Thanks in advance!

---

### Post by Frogs Hair on 2017-06-12
Can you link the themes you are trying to use ? Also , make sure the themes are fully extracted and not in a master folder. If not fully extracted the themes can be visible in the tweak tool but will not apply. Some 3rd party themes will only work in the Gnome DE.

---

### Post by adamhff on 2017-06-12
Ok here is the theme: [https://blog.anmoljagetia.me/flatabulous-ubuntu-theme/](https://blog.anmoljagetia.me/flatabulous-ubuntu-theme/) and [https://github.com/anmoljagetia/Flatabulous](https://github.com/anmoljagetia/Flatabulous) for good measure. 
Here is the icon set: [http://www.noobslab.com/2015/01/make-linux-more-elegant-with-ultra-flat.html](http://www.noobslab.com/2015/01/make-linux-more-elegant-with-ultra-flat.html)

I think I installed them via command line, like: [COLOR=#333333][FONT=Ubuntu]sudo apt-get install ultra-flat-icons - they show up in unity tweak tool and when I click to apply it SOME of the colors get changed, same with the icons, SOME get changed. - It was easier for me to install them via command line, could that be the problem? Not sure where I would get the icon set folder at, I see the theme on github though. 

I would be open to trying ANY theme, however. Maybe you could point me to a decent theme that you know works? I could use it as a benchmark.

I am using unity, btw, and thanks for the response![/FONT][/COLOR]

---

### Post by Frogs Hair on 2017-06-13
What Ubuntu release ? I was able to install the linked theme  and it works installed in .themes , but it is broken due to the release I'm using. The icons do install and display properly though I grabbed the .deb package from the Noobslab launchpad page  rather than use the PPA.

 [https://launchpad.net/~noobslab/+archive/ubuntu/icons/+packages?batch=75&memo=300&start=300](https://launchpad.net/~noobslab/+archive/ubuntu/icons/+packages?batch=75&memo=300&start=300)

---

### Post by adamhff on 2017-06-13
I'm using 16.04. - Does it change your entire ubuntu theme? even the very top menu bars? I just don't know what could be causing this. Like I originally asked, is there a way of getting themes in the default ubuntu theme selector? Like with ambiance and radiance? Those seem to work. IT does seem like it's broken.

---

### Post by deadflowr on 2017-06-13
> is there a way of getting themes in the default ubuntu theme selector? 
Do you mean the selector in the System Settings: Appearance section?
Then no, that is hard-coded.

---

### Post by Frogs Hair on 2017-06-13
> [COLOR=#000000]I'm using 16.04. - Does it change your entire ubuntu theme? [/COLOR]

Yes, the top panel and title bars change, but context menus and file manager side panel are broken only because I'm using gnome 3.24.

---

### Post by adamhff on 2017-06-13
Ok so I have to use unity tweak tool or gnome tweak. If I changed from unity to gnome would it work? I might try that, I would have to customize the crap out of it because I don't like gnome's default appearance. Still wondering what is causing this.

---

### Post by Frogs Hair on 2017-06-13
The theme you linked is supposed to work in Unity on 16.04. Try the following commands .  

```
sudo apt-get install dconf-tools
``` ```
dconf reset -f /org/compiz/
```

---

### Post by again? on 2017-06-13
@**adamhff**
```
glen@Xen2:~$ lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

_Default icons/theme_
[[img]https://s19.postimg.org/l95ozova7/095.jpg[/img]](https://postimg.org/image/l95ozova7/)

_Your linked icons/theme_
[[img]https://s19.postimg.org/sqjhsna73/096.jpg[/img]](https://postimg.org/image/sqjhsna73/)

gtk theme changes are applied immediately.
You may need to run "**unity**"  in the terminal to reload icons in the launcher/panel.
Some applications include there own icons and won't change with an icon theme change.

---

### Post by adamhff on 2017-06-14
Oh heck yes! The dconf reset worked! Thank you SO MUCH! Hopefully this works with all themes/icons now. - What exactly did that do?

Thanks again!

---

### Post by deadflowr on 2017-06-14
the dconf reset command reset the desktop to it's default settings.
purging out any of the setting you may have set, knowingly or not.

---

### Post by Frogs Hair on 2017-06-14
> **adamhff said:**
> Oh heck yes! The dconf reset worked! Thank you SO MUCH! Hopefully this works with all themes/icons now. - What exactly did that do?

Thanks again!

You're  Welcome !

---

### Post by adamhff on 2017-06-25
Ok so that worked for a couple reboots/shutdowns but now the theme/icons are back to not working. They work sometimes after redoing the dconf reset and rebooting, but every other reboot I have to do that again and even the dconf reset doesn't always work!

It seems that even with things like my mp3 player (tomahawk and/or rhythmbox) that not many of my settings get saved. Everytime I reboot or shutdown I have to put in my music folder and rescan my music collection for my music to show up.

Any further ideas?

Thanks

---

