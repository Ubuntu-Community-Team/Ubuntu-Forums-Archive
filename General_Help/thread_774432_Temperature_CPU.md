---
title: "Temperature CPU"
date: 2008-04-29
forum: General Help
---

### Post by Cooler1989 on 2008-04-29
How can I check temp CPU on Hardy Heron. Lm-sensors don't work. :/

---

### Post by Monicker on 2008-04-29
> **Cooler1989 said:**
> How can I check temp CPU on Hardy Heron. Lm-sensors don't work. :/

The way I do it on my laptop is to use yacpi from a terminal.  You can also try "acpi -t".

---

### Post by Cooler1989 on 2008-04-29
> **Monicker said:**
> The way I do it on my laptop is to use yacpi from a terminal.  You can also try "acpi -t".

```
acpi -t
No support for device type: thermal
```

---

### Post by GCoffee on 2008-04-29
I use the gnome sensors applet... Can't remember where I got it, sorry..

I then scanned using lm-sensors by accident and It tells me my fan revoloutions cpu temps everything.

---

### Post by jespdj on 2008-04-29
You can install the GNOME sensors applet by installing the package sensors-applet:
```
sudo apt-get install sensors-applet
```
After that, logout and login again, right-click the top panel on the desktop, select "Add to Panel...", and choose "Hardware Sensors Monitor".

Right-click the applet and select Preferences to choose the sensors that you want to monitor.

---

### Post by Cooler1989 on 2008-04-30
Ok thanks it works but I have problem with ID of this temperatures.
Temp of what shows Temp Power and why it shows 126*C

---

### Post by chunchengch on 2008-04-30
There is a computer temperature monitor applet in the Hardy repository, just run command to install it:

[COLOR="Red"]$ sudo apt-get install computertemp[/COLOR]

then right-click the top panel on the desktop, select "Add to Panel", and choose "Computer Temperature Monitor", that's it!

---

### Post by AlesUbu123 on 2008-07-01
sorry i have accidentaly posted this reply to a wrong thread. 
disregard it please

---

