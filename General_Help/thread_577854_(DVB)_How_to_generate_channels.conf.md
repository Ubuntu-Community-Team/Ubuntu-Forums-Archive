---
title: "(DVB) How to generate channels.conf?"
date: 2007-10-16
forum: General Help
---

### Post by Bou on 2007-10-16
Hi,

I have recently bought a WinTV Nova-T DVB card to watch DVB. The software I'm using, though (me-tv) complains that there is no "channels.conf" file.

I've taken a look at the example files and found [some]("http://www.tdt.es/TDT/Detalles?CP=12005&pob=CASTELLON%20DE%20LA%20PLANA&vIdPob=0") [pages]("http://www.tdt1.com/canales-television-castellon.php") with info on the channels available in my city, but I have no idea what I have to do with that information.

How can I create a working file?

Thanks in advance.

---

### Post by Total_Biscuit on 2007-10-16
Quick answer:
[LIST=1]
[*]Try kaffeine because it has channel scan capability and doesn't need a channels.conf.
[*]Install the dvb-utils package, browse through /usr/share/doc/dvb-utils/examples/scan/dvb-t/ to see if there is a suitable initial tuning data file for your nearest transmitter (es-Alfabia, es-Alpicat, es-Collserola, es-Lugo, es-Madrid, es-Mussara, es-Rocacorba and es-Sevilla are provided - I have no idea which one, if any, will work for your location) and then run
```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/es-ChosenDataFile > channels.conf
```
[/LIST]

---

