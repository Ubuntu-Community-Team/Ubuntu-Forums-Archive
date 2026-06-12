---
title: "rrdtool graph"
date: 2015-08-04
forum: General Help
---

### Post by dozycat on 2015-08-04
I am trying to graph a derive rrd from a backup.
I can generate the graph with rrdtool but the values are wrong, the instruction is the following:

rrdtool graph test.png --imgformat PNG   --start end-2d --end 00:00    --width 600    --height  300 \
DEF:ds0a=prueba.rrd:down_prio:AVERAGE  DEF:ds0b=prueba.rrd:up_prio:AVERAGE \
DEF:ds0c=prueba.rrd:down_dfl:AVERAGE DEF:ds0d=prueba.rrd:up_dfl:AVERAGE CDEF:new1=ds0a,8,*, \
CDEF:new2=ds0b,8,*,  CDEF:new3=ds0c,8,*, CDEF:new4=ds0d,8,*, LINE1:new1#32CD32:"down\l" \
CDEF:total=PREV,UN,0,PREV,IF,new1,+  GPRINT:new1:MAX:"Max %6.2lf %s" \
LINE1:new3#7CFC00:"down p2p\l" LINE1:new2#FF0000:"up\l"  LINE1:new4#FFA500:"up p2p\l" \
 LINE1:total#FF0000:"down\l"

The rrd file is in derive so I need to know how to calculate the original values, the line CDEF:total=PREV,UN,0,PREV,IF,new1,+  GPRINT:new1:MAX:"Max %6.2lf %s" , is not working.

---

