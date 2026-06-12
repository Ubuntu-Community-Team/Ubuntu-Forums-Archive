---
title: "Best weather indicator"
date: 2014-08-17
forum: General Help
---

### Post by fizikz on 2014-08-17
What are the best or favorite weather apps, applets, indicators available for Ubuntu 14.04? Preferably something with a small, unobtrusive icon that fits nicely in the gnome panel (flashback). 

I had a nice indicator in 12.04 but I don't remember what it was called anymore and after upgrading to 14.04 it is gone. It showed an icon for sunny/cloudy/rainy/etc with the temperature printed next to it. clicking on it popped up a window with more detailed information. Surely something like this exists for 14.04?

---

### Post by CantankRus on 2014-08-18
For a panel indicator install [**_[COLOR="#B22222"]my-weather-indicator[/COLOR]_**]("https://launchpad.net/~atareao/+archive/ubuntu/atareao")

---

### Post by fizikz on 2014-08-18
Thanks! I actually just finished installing my-weather-indicator and I'm really impressed with the range of information, maps, weather evolution option, and the overall quality of the indicator.

Out of habit, I would just like to put the taskbar icon centered on the gnome panel independent of other notification applets/icons. Is this possible?

The only other indicator I found is indicator-weather, but I did not even get to install it as the PPAs gave 404 errors when doing "sudo apt-get update". [http://www.webupd8.org/2013/05/install-weather-indicator-with-new.html]("http://www.webupd8.org/2013/05/install-weather-indicator-with-new.html")

---

### Post by CantankRus on 2014-08-18
Last build in the indicator-weather ppa was for saucy.
Much the same as the one you have installed anyway.

The my-weather-indicator is a unity style indicator and as such is shown in the **indicator applet complete** for gnome-panel.
You can only position the applet not individual indicators shown within the applet.

---

### Post by fizikz on 2014-08-18
Would it be possible to have a second, independent **indicator applet complete** populated only with my-weather-indicator and centered on gnome-panel?

---

### Post by CantankRus on 2014-08-18
No because you can't configure the order or what's shown for each individual applet..
It will just be a duplicate.

---

### Post by fizikz on 2014-08-18
Ok, thanks, CantankRus.

I believe we have a winner. my-weather-indicator is the best and seemingly only weather indicator. For the purpose of this thread, I'll consider this SOLVED.

---

### Post by hako1 on 2015-05-07
> **fizikz said:**
> Ok, thanks, CantankRus.

I believe we have a winner. my-weather-indicator is the best and seemingly only weather indicator. For the purpose of this thread, I'll consider this SOLVED.

Unfortunately, my-weather-indicator does not work in China, probably because of the Great China Firewall.
The program does not even open up to set its preferences.
I had indicator-weather running on 14.04 before I did a fresh install with 64 bit. Its ppa throws a 404, now.

That means, there is no weather indicator for Ubuntu which can be used in China. (Possibly with the exception of a Chinese only weather app which I cannot read)

I just tried with the deb of indicator-weather and pywapi which I downloaded from its website. It is a little complicated, but it works with 14.04 64 bit in China (I set the weather source to Yahoo).

---

