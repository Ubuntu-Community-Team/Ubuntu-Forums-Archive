---
title: "Wallpaper changer"
date: 2013-05-16
forum: General Help
---

### Post by garyzw on 2013-05-16
I am using Ubuntu 13.04 Raring Ringtail. I like the rotating wall papers and would like to know how to add wall papers and make them change like the ones in Ubuntu. Is this a script? Or how is it done?

---

### Post by Megaptera on 2013-05-17
Have you considered Wallch? Quote from link below: "Wallch is a wallpaper changer for Gnome which can change the desktop wallpaper after an adjustable time. It has a friendly and easy to use graphical interface. Wallch also supports Live Earth wallpaper which updates every 1/2 hour."
Not sure about 13.04 but this guide may help: [http://www.noobslab.com/2012/05/install-wallch-wallpaper-changer-in.html](http://www.noobslab.com/2012/05/install-wallch-wallpaper-changer-in.html)

---

### Post by deadflowr on 2013-05-17
It is a basic xml script.
Look in /usr/share/backgrounds for the images.
And /usr/share/gnome-background-properties for the xml files.
Look at the raring-wallpaper.xml file and the rotating wallpaper will be the first entry
```
<wallpapers>  <wallpaper deleted="false">
    <name>Ubuntu 13.04 Community Wallpapers</name>
    <filename>/usr/share/backgrounds/contest/raring.xml</filename>
    <options>zoom</options>
  </wallpaper>
```

Then look in the xml file in the backgrounds folder.

It'll make sense if you look at it for a minute.

Remember the time is set for seconds.

---

### Post by garyzw on 2013-05-17
> **Megaptera said:**
> Have you considered Wallch? Quote from link below: "Wallch is a wallpaper changer for Gnome which can change the desktop wallpaper after an adjustable time. It has a friendly and easy to use graphical interface. Wallch also supports Live Earth wallpaper which updates every 1/2 hour."
Not sure about 13.04 but this guide may help: [http://www.noobslab.com/2012/05/install-wallch-wallpaper-changer-in.html](http://www.noobslab.com/2012/05/install-wallch-wallpaper-changer-in.html)

Yes I tried that but it seems the app has to be running in the background to work-- otherwise it works great

---

### Post by garyzw on 2013-05-17
> **deadflowr said:**
> It is a basic xml script.
Look in /usr/share/backgrounds for the images.
And /usr/share/gnome-background-properties for the xml files.
Look at the raring-wallpaper.xml file and the rotating wallpaper will be the first entry
```
<wallpapers>  <wallpaper deleted="false">
    <name>Ubuntu 13.04 Community Wallpapers</name>
    <filename>/usr/share/backgrounds/contest/raring.xml</filename>
    <options>zoom</options>
  </wallpaper>
```

Then look in the xml file in the backgrounds folder.

It'll make sense if you look at it for a minute.

Remember the time is set for seconds.

This is something more of what I was looking for-- Thanks

I also found a nice script that does all the work for you--

[http://www.webupd8.org/2011/12/create-wallpaper-slideshow-with-xml.html](http://www.webupd8.org/2011/12/create-wallpaper-slideshow-with-xml.html)

---

