---
title: "MRTG Watts values from snmp server"
date: 2013-11-23
forum: General Help
---

### Post by logman on 2013-11-23
Hi,

I trying to set up **mrtg **watts reading, i have snmp server where i do get readings but somehow mrtg does not do it right...

```
 
UCD-SNMP-MIB::extOutput.5 = STRING: **275**

```

```

Target[UPS-OutputW]: 1.3.6.1.4.1.2021.8.1.101.5**&**1.3.6.1.4.1.2021.8.1.101.5:public@192.168.0.2
Directory[UPS-OutputW]: apc
Options[UPS-OutputW]: growright, gauge, nopercent, absolute
Title[UPS-OutputW]: Watts
YSize[UPS-OutputW]: 200
ShortLegend[UPS-OutputW]:
YTics[UPS-OutputW]: 10
YLegend[UPS-OutputW]: Load (Watts)
LegendI[UPS-OutputW]: Load
LegendO[UPS-OutputW]:
PageTop[UPS-OutputW]: <H1> UPS: Output Load (Watts) </H1>

```

I only get this kind info on Watts usage..

[IMG]https://dl.dropboxusercontent.com/u/22611414/ubuntu/watts.jpg[/IMG]

---

