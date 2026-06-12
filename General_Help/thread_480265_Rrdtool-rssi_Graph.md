---
title: "Rrdtool-rssi Graph"
date: 2007-06-21
forum: General Help
---

### Post by hayouta on 2007-06-21
Hi,


I've followed the instructions on [http://martybugs.net/wireless/rrdtool/](http://martybugs.net/wireless/rrdtool/) 
concerning "Wireless Link Monitoring with RRDTool" ,I used the script but I deleted the lines corresponding to SNR and link rate as I only want to disply the signal value in dBm. 
To obtain data I've replaced the "iwconfig" command by "snmpget" and this works well,and here is the result: 
 
[COLOR="Blue"]linux:~ # snmpget -c public -v 1 192.168.111.10 1.3.6.1.4.1.7262.1.16.6.0 -Oqv 
-511 [/COLOR] 
as you see the result the RSSI value is negative and multiplied by 10 :-511
You could have a look at the script (attached file)
 
When I runned the script that works fine and finds the rssi value:
[COLOR="blue"]linux:~ # /usr/local/bin/rrd_wlan.pl

192.168.111.10 link stats: signal: -519 dBm[/COLOR]
But unfortunately the obtained graph does not show the RSSI values ,please have a look at the graph in the attached file.

I'd be so thankful.

Regards

---

