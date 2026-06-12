---
title: "Shell Script"
date: 2008-04-27
forum: General Help
---

### Post by hardhittertennis on 2008-04-27
Hey, im new to ubuntu (or anything different from windows) and i dont have sound because i have the xtremegamer creative sound card. I downloaded the linux drivers and am trying to run the shell script, but when i do it in the terminal i get this error
___________________________________________________________________

configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

___________________________________________________________________

I have no idea what to do but any help would be great!

Link to driver

[http://us.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+XtremeGamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&drivertype=1&x=15&y=13](http://us.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+XtremeGamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&drivertype=1&x=15&y=13)

---

### Post by mali2297 on 2008-04-27
My guess is that you need the package **build-essential**. In the terminal, run
```

sudo apt-get install build-essential

```
or install the package via Synaptic.

---

