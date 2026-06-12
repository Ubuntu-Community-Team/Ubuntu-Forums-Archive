---
title: "[ubuntu][20.04 LTS] Weather applet not showing forecast"
date: 2021-03-17
forum: General Help
---

### Post by georgesgiralt on 2021-03-17
Hello !
Since a fortnight, (approx.) my weather applet is not showing any weather forecast. Only the current temp and cloud/rain status. 
I live in France so look at French cities weather forecast. It is all the same whatever location I use. 
The applet identifies itself as "Météo" version 3.36.1 and it seems to use the packages : 
```

ii  gir1.2-gweather-3.0:amd64                     3.36.1-1~ubuntu20.04.1                     amd64        GObject introspection data for the GWeather library
ii  gnome-shell-extension-weather                 0~20170402.git34506a6-2                    all          weather extension for GNOME Shell
ii  gnome-weather                                 3.36.1-1                                   all          access current conditions and forecasts
ii  libgweather-3-16:amd64                        3.36.1-1~ubuntu20.04.1                     amd64        GWeather shared library
ii  libgweather-common                            3.36.1-1~ubuntu20.04.1                     all          GWeather common files

```
I've tried to reinstall all the avove mentioned packages but to no avail. 
As I use the standard Gnome shell (version 3.36.4 ) I tried looking at the Gnome shell extension page. It shows an "ERROR" red flag on the OpenWeather extension item.  (as this is a "system extenson" control are pretty limited on this one..
For now, I'm at sea, lost. So all help I can get will be vasty appreciated. 
Many thanks in advance for your help. 
P.S. : I've tried all Paris, Lyon, Marseille, and Toulouse locations I know of with the same result.

---

### Post by Autodave on 2021-03-17
Go here and download the file.  [http://repo.linuxliteos.com/linuxlit....0-1_amd64.deb]("http://repo.linuxliteos.com/linuxlite/pool/main/x/xfce4-weather-plugin/xfce4-weather-plugin_0.11.0-1_amd64.deb")  The only problem that I had was that the software installer refused to install this file on 2 different machines and I had to use *gdebi* to install it.  *gdebi* is avaialble in the repositories.

---

### Post by georgesgiralt on 2021-03-17
OK, I downloaded it and installed it. Still no forecast. What else should I do as it is an XFCE package and I use Gnome ?

---

