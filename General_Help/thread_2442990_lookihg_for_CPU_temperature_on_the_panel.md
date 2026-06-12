---
title: "lookihg for CPU temperature on the panel"
date: 2020-05-10
forum: General Help
---

### Post by jarp53 on 2020-05-10
I'm using Xubuntu 20.04 , and I'm looking to monitor my CPU temperature on the panel with out having to click any thing , I have it on the Fxce  panel of LMDE 4 , does any body what I can use ?  ( thank you )

---

### Post by dino99 on 2020-05-10
[https://www.tecmint.com/monitor-cpu-and-gpu-temperature-in-ubuntu/](https://www.tecmint.com/monitor-cpu-and-gpu-temperature-in-ubuntu/)

---

### Post by Holger_Gehrke on 2020-05-10
The package 'xfce4-sensors-plugin' might be what you're looking for. According to packages.ubuntu.com it's in the universe repository for 20.04.

Holger

---

### Post by Artim on 2020-05-10
One of the first things I do in a new install of Xubuntu is 

```
 sudo apt-get install synaptic 
```

Because it's easily searchable with descriptions for just what I need.  Xfce4-sensors-plugin is a panel app that you can add to a panel to display the temperature, CPU load, etc.

---

### Post by jarp53 on 2020-05-10
thank you all ; [[COLOR=#000000]Holger_Gehrke[/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")[COLOR=#000000] 's is working good , it did had an error at first but it also offer the solution which was to run < chmod u+s /usr/sbin/hddtemp > as root , and with done is working great so thanks again [/COLOR]

---

