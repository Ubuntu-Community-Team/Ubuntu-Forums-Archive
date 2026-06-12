---
title: "Can't install any indicators in the unity panel - Ubuntu 13.04"
date: 2013-06-13
forum: General Help
---

### Post by lacouf on 2013-06-13
What use to work fine in Ubuntu 12.04 is not working at all in 13.04

I tried:
```

sudo apt-get install indicator-multiload

```

Also tried with these indicators
```

sudo apt-get install indicator-applet-appmenu
sudo apt-get install indicator-applet-session

```

And still,  NO indicators are showing up in my unity panel.  

Does anybody else have that issue ?

---

### Post by grahammechanical on 2013-06-13
I am using Saucy Salamander (under development). I think that you will find that indicator session and indicator appmenu are already installed. There are in the Software Centre as Indicator showing session Management, status and user switching, and Indicator for application menus.

I have also just used the software Centre to install system load indicator (also called indicator-multiload) and it does not appear in the top panel until it is launched from the Dash. That action should then put it as a startup application. You can also find Startup Applications in the Dash and see what startup applications are in use.

Regards.

---

### Post by Frogs Hair on 2013-06-13
I can confirm multiload needs to be started  from dash  and indicator-session and appmenu are default although  [COLOR=#000000][FONT=Ubuntu Mono]indicator-applet-session and appmenu also appears in synaptic.[/FONT][/COLOR]

---

