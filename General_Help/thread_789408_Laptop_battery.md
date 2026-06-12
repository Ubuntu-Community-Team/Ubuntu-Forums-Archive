---
title: "Laptop battery"
date: 2008-05-10
forum: General Help
---

### Post by ProfKaramba on 2008-05-10
Hi

When I'm using ubuntu 8.04 my battery only lasts 40minutes... and the laptop gets really hot

I have a LG P1.

What can I do?

---

### Post by ghost_ryder35 on 2008-05-10
possibly bad battery, how old is it?. try using the live cd and see how long it lasts. to help prolong battery life dim the laptop display

---

### Post by ProfKaramba on 2008-05-10
when I'm using windows XP it lasts more than 2h. The laptop has 1year

---

### Post by minus198 on 2008-05-10
sudo apt-get install powernowd

Then add CPU Frequency Monitor Preferences to a panel in Gnome.

Press alt + f2 and type: "gconf-editor" -> press enter.

Go to "app" -> gnome-power-manager -> cpufreq -> edit policys to "ondemand".

This will enable CPU throttling which will clock down your CPU while the power isn't needed. This will make the battery to last longer. 

And also, as another person said, you can lower the monitorbrightness while you don't need it.

---

### Post by ProfKaramba on 2008-05-10
it was already ondemand...

---

### Post by bomanizer on 2008-05-10
laptop-mode?

```
$ cat /etc/default/acpi-support | grep LAPTOP
ENABLE_LAPTOP_MODE=true

```

Open that file with an editor and change the value from "false" to "true".

At least with Gutsy the default value is "false", go figure... :rolleyes:

---

### Post by ProfKaramba on 2008-05-10
yes it was false...
let's see :)

Thank you

---

### Post by ProfKaramba on 2008-05-11
the problem continues... Less than 1h of battery time!

---

### Post by brigadoon on 2008-05-11
It sounds like your operating system needs to learn the battery. Drain and recharge the battery completely several times. When the battery is draining a power icon should appear next to the clock on the desk top. Right click it and select the ***Power History*** option. Check out the various graph types. The last two graphs list discharge and charge accuracy. Keep draining and recharging till you get close to 100% accuracy.

Drain the battery once a month. Recharge fully. Laptops need to do this to manage the battery accurately.

---

