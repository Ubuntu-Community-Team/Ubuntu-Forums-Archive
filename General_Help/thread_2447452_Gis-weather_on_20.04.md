---
title: "Gis-weather on 20.04"
date: 2020-07-19
forum: General Help
---

### Post by shantiq on 2020-07-19
just moved on to 20.04


and for the fans of Gis-weather weather app
found that the only service which works is Gismeteo which is triggered with a number found on the Gismeteo site


the quickest way to install is to remove your older gis-weather folder in home folder if you upgraded from say 18.04


```
cd && git clone https://github.com/RingOV/gis-weather.git && cd gis-weather/scripts && python3 build_deb.py && cd ../DEB && sudo dpkg -i *.deb
``` 


and then pick gismeteo with your town number


[[IMG]https://i.postimg.cc/sQ9TqP6F/g.png[/IMG]]("https://postimg.cc/sQ9TqP6F")


PS current version August 2020 is 0.8.4.13

---

