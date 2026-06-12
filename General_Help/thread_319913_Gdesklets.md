---
title: "Gdesklets"
date: 2006-12-16
forum: General Help
---

### Post by CheeseQueen452 on 2006-12-16
I installed Gdesklets & tried to set up a weather desklet, but it can't retrieve my local weather data. How do I get it to work?

---

### Post by hadiriazi on 2006-12-16
> **CheeseQueen452 said:**
> I installed Gdesklets & tried to set up a weather desklet, but it can't retrieve my local weather data. How do I get it to work?

I've got the same problem :(

---

### Post by timetunnel on 2006-12-17
In Edgy, all weather applets seem to be broken and they don't show any data. I read about that somewhere but don't remember where. The only weather applet that works is the "GoodWeather" applet, which is not in the ubuntu repository but available at:
[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)

To install:
[LIST]
[*]start gdesklets
[*]right-click on its icon and select "manage desklets" (or something like that, I have it in German only)
[*]choose the menu item under "file" which is for installing remote files ("install non-local file" or "install remote file" or something like that)
[*]enter the URI [http://gdesklets.zencomputer.ca/GoodWeather.tar.gz](http://gdesklets.zencomputer.ca/GoodWeather.tar.gz)
[*]the package will be downloaded and installed (no root priveleges needed, it will be installed to your home folder)
[*]Done. It will not appear in the category "Weather" but in "uncategorized"
[/LIST]

After you've started the GoodWeather applet you have to get the "location code".
[LIST]
[*]Go to [http://weather.yahoo.com](http://weather.yahoo.com) and find your city
[*]the URL will look like this (this one is for Berlin): [http://weather.yahoo.com/forecast/GMXX0007.html](http://weather.yahoo.com/forecast/GMXX0007.html)
[*]the "location code" is the right-most part of the URL without the file extension, in this example "GMXX0007
[*]That's it.
[/LIST]

It's running fine on my system, however, sometimes it seems like it's not updating the weather data until the applet is started again.

Jens

---

### Post by CheeseQueen452 on 2006-12-17
Hmm, that's interesting. I wonder why they don't work in 6.10? Anywho, thanx for letting me know.

---

### Post by djlyx on 2006-12-18
Hi, great write-up

do you know how I can auto start appletts, so that when I start my computer it automatically displays the weather?

thanx

---

### Post by djlyx on 2006-12-18
Wait nevermind I figured it out.

Go to "autostarted applications" click "add" and type "gdesklets" as the command.

Bada Bing!

---

