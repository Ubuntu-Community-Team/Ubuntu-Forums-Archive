---
title: "TLP, Lenovo X200"
date: 2014-10-20
forum: General Help
---

### Post by nico25 on 2014-10-20
[COLOR=#1D1212][FONT=sans-serif]Every time I use the "**STOP_CHARGE_THRESH_BAT0=80**" on the **/etc/default/tlp** config file, my battery just stops charging no matter what %. 
I commented the line **#START_CHARGE_THRESH_BAT0=55** but no effect, and i have no clue whats causing this. 
If I comment the STOP_CHARGE line and reboot, battery still wont charge, but if i use the command "** tlp fullcharge**" then its back to normal. 
Currently running **kernel: 3.13.0-38 | Lenovo X200**
Any help is appreciated.[/FONT][/COLOR]

---

### Post by linrunner on 2014-10-21
Hi,

the proper procedure to remove thresholds is in the FAQ --> [http://linrunner.de/en/tlp/docs/tlp-faq.html#how-to-disable-thresholds](http://linrunner.de/en/tlp/docs/tlp-faq.html#how-to-disable-thresholds)

If you want to keep only the upper threshold, just configure
```

#START_CHARGE_THRESH_BAT0=55
STOP_CHARGE_THRESH_BAT0=80 

```
and then give
```
sudo tlp fullcharge # remove all thresh
sudo tlp setcharge # set upper thresh
```

Please show the complete output of
```
sudo tlp-stat
```

---

