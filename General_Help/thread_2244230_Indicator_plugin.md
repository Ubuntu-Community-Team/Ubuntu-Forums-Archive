---
title: "Indicator plugin"
date: 2014-09-14
forum: General Help
---

### Post by timmyk.2 on 2014-09-14
Greetings. I feel a little dumb for posting this, but how do I change what is diplayed in the indicator plugin on my panel? I'd really like to get rid of the clock, screen brightness applet, and bluetooth icon. I've looked through all the panel settings but I can't seem to be able to find a way to change this.

---

### Post by CantankRus on 2014-09-14
Install dconf-editor and look in **com.canonical.indicator**

---

### Post by timmyk.2 on 2014-09-14
Thanks, that got rid of the clock, but the Bluetooth is still there whether I check the "visible" box or not. Also, I've a brightness indicator that I installed by typing
```
sudo apt-get install indicator-brightness
```
but couldn't get rid of, even with 
```
sudo apt-get remove indicator-brightness
```

---

### Post by CantankRus on 2014-09-14
What desktop does ubuntu-studio use nowadays?
```
echo $DESKTOP_SESSION
```

---

### Post by timmyk.2 on 2014-09-14
It just says "ubuntustudio". Are you wondering about the desktop enviroment? It's XFCE.

---

### Post by CantankRus on 2014-09-15
Ok, I don't use XFCE though I have it installed.
The settings in dconf under com.canonical.indicator relate to indicators shown in a unity notification area.

eg in XFCE I have installed **xfce4-indicator-plugin** which puts the unity style indicator to the xfce panel.
For what shows in your xfce panel systray I don't know how you control those other than in the app preferences itself
or totally remove the systray from the panel.

---

