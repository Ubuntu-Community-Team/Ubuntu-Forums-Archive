---
title: "SOLVED - System program problem detected"
date: 2013-05-16
forum: General Help
---

### Post by bone2006 on 2013-05-16
I'm running Lubuntu and wanted an application like f.lux, which I found out about redshift.  I installed redshift and then running redshift the application wouldn't run and I would get a system program probluem detected pop up.    

Well I found out I could just run the lat and lon in the command line, so I type this command
redshift -l X:Y

redshift appears to run just perfectly and I don't have any issues, except O keep getting the pop up of system program problem detected, which is getting annoying.

I went into ~/.config/autostart and put a redshift.desktop file with the command, so that redshift would start automatically every time.    So now I'm getting the popup every time I reboot.  Only the popup is annoying me, but I don't see anything wrong with redshift or any other issues.  I'm not sure how to figure out why I'm getting this pop up or how to stop it for redshift, if it's working fine in LXDE for me right now

Any help is appreciated

---

### Post by ibjsb4 on 2013-05-16
Could it be?

[http://ubuntuforums.org/showthread.php?t=2145471&p=12649760#post12649760](http://ubuntuforums.org/showthread.php?t=2145471&p=12649760#post12649760)

also

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=System+program+problem+detected&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=System+program+problem+detected&sa=Search&cof=FORID:9)

---

### Post by bone2006 on 2013-05-16
thanks for the reply, but  I didn't have any detail options.  I'm guessing that's enabled in gnome.

I removed the content in crash folder and it no longer popups up

$ sudo rm /var/crash/*

---

