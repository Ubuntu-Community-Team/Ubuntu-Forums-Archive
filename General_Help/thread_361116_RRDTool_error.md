---
title: "RRDTool error"
date: 2007-02-14
forum: General Help
---

### Post by NinTniN on 2007-02-14
I installed cacti and created a device, but my graphs does not want to display. When I run debug mode, I get the following message:

RRDTool Command:

/usr/bin/rrdtool graph - \
--imgformat=PNG \
--start=-86400 \
--end=-300 \
--title="Test one - CPU Usage" \
--rigid \
--base=1000 \
--height=120 \
--width=500 \
--alt-autoscale-max \
--lower-limit=0 \
--vertical-label="percent" \
--slope-mode \
DEF:a="/usr/share/cacti/site/rra/test_one_5min_cpu_8.rrd":5min_cpu:AVERAGE \
AREA:a#FF0000:"CPU Usage"  \
GPRINT:a:LAST:"Current\:%8.0lf"  \
GPRINT:a:AVERAGE:"Average\:%8.0lf"  \
GPRINT:a:MAX:"Maximum\:%8.0lf" 

RRDTool Says:

ERROR: opening '/usr/share/cacti/site/rra/test_one_5min_cpu_8.rrd': No such file or directory


When I go and look at the directory "/usr/share/cacti/site/rra/test_one_5min_cpu_8.rrd" it shows that the directory rra is actualy a shortcut to "/var/lib/cacti/rra". Anybody got some info for me???? Thanks guys and gals.

---

