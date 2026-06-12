---
title: "Is There A Progam that:"
date: 2013-01-21
forum: General Help
---

### Post by fredmt on 2013-01-21
That changes the background picture everytime (anytime?) computer is botted?

---

### Post by Cheesehead on 2013-01-21
What, precisely, do you mean by 'botted'? One fellow I know means 'infected by malware', another means 'defeated in a game by the computer player', another means 'ssh port probed'

You can easily change the desktop picture, or do almost anything else, in response to almost any measurable criteria.

Generally, you don't need a whole application to do it. A few lines of shell script to see if the criteria passes your threshold value are enough.

---

### Post by ibjsb4 on 2013-01-21
botted = booted ?

Yes, but I have not used wallpapers in a long while so don't remember which package did it.  Here's a couple of places to look.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wallpaper+changer&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wallpaper+changer&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+wallpaper+at+boot&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+wallpaper+at+boot&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Impavidus on 2013-01-21
In xfce I use the following lines:```

for session in $HOME/.dbus/session-bus/*; do
    export `grep ^DBUS_SESSION_BUS_ADDRESS $HOME/.dbus/session-bus/$session`
    xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path \
        -s $HOME/images/image1.jpg 2>> $logfile
done
```with some extra code for downloading a new picture every hour (live weather satellite images).

You'll have to figure out how to change this to get it working in unity. The for loop with the dbus session address and the export on the next line are meant to get it running as a cron job, you can skip that if you're using it as login script. Also, changing the picture to one with the same file name doesn't work (unless somebody tells me right now how to do it), so I alternate between two names. I redirect error messages to a log file.

Just to give you an idea of how to do this.

---

### Post by Frogs Hair on 2013-01-21
Variety is a wallpaper changer application , but I don't know if the settings include change at boot.  [http://www.webupd8.org/2012/11/variety-wallpaper-changer-sees-new.html](http://www.webupd8.org/2012/11/variety-wallpaper-changer-sees-new.html)

---

### Post by fredmt on 2013-01-21
If you gentlemen would bare with me in my ignorance but unforntunately, I have no form of programming experience (have several books and even tried teaching myself but to no avail: wish there was a channel that start from the very beginning and walk one through the process but this is not the time or palce for that; Besides, most people assume you have some form of experience because you ask the question). However, I am simply looking for a program that I can point to my /picture folder and have it change the background image ever so often; atleast, whenever my computer is booted.

Thanks for all of your help!

PS: I have installed Variety & Wallach; and will play with these. Once again, thanks gentlemen!

PS: PS: & Grub-Customizer BUT I do not know enough about the booting process to mess with it. Perhaps after doing additional reading (another year?)

---

### Post by oldos2er on 2013-01-21
Maybe this will get you started? ```
apt-cache search wall paper changer

cortina - Wallpaper changer for gnome
wallch - Automatic Desktop Wallpaper Changer
wally - Qt4 wallpaper changer
variety - automatic wallpaper changer, downloader and manager.
syncwall - Wallpaper changer
```

You can also use Software Center to search for programs, if you prefer.

---

