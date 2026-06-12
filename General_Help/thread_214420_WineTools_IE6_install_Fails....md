---
title: "WineTools IE6 install Fails..."
date: 2006-07-12
forum: General Help
---

### Post by pbjorge12 on 2006-07-12
Hey!
I'm running a "near" clean install of Dapper Drake with wine 0.9.9 installed. I was trying to use WineTools to install IE6 but it fails EVERY time...

I was looking at Wine's appdb and saw that IE6 was supported as "garbage..." Is this why the install failed? Will it be back in working order soon?

---

### Post by lanhelp on 2006-07-12
use the deb source from winehq.com: 
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


sudo apt-get update
sudo apt-get install wine

Worked for me.

Good luck!

---

### Post by mostwanted on 2006-07-12
[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

Works wonders.

---

### Post by shanepardue on 2006-07-12
you must install an older version of wine to use winetools. after you install the following version, install winetools, then upgrade your wine to use a current version of wine.

```
wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```

---

### Post by Billquinn1 on 2006-07-13
Or don't upgrade. If you do, it may break IE again and then you will have to go in and force the older version. I've had good and bad luck there. If the .5 version does everything you need, go into synaptic and lock the version.

---

### Post by Jagot on 2006-07-13
> **mostwanted said:**
> [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

Works wonders.

I'll second that.

---

### Post by punkass on 2006-07-13
> **Jagot said:**
> I'll second that.

And I'll third it.

---

### Post by hollaburoo on 2006-07-14
> **punkass said:**
> And I'll third it.

And I'll fourth it

---

### Post by jimmygoon on 2006-07-14
Why is everyone so insistant upon using WineTools... this is much better!!!

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

