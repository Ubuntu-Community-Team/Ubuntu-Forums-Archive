---
title: "rsyslog template filter"
date: 2022-05-16
forum: General Help
---

### Post by gomezz2022 on 2022-05-16
Hello,

I have my syslog setup to receive traffic logs from panorama device that forwarding me all firewall logs of my managed devices.
The objective is to create a seperate log file based on the firewall hostname include in the log files( important not the same as the sending hostname, ip of the logs)

Example log file:

2022-05-16T14:26:01+00:00 PANORAMA 1,2022/05/16 14:26:01,012001050280,TRAFFIC,end,2049,2022/05/16 14:25:57,10.51.10.8,10.52.2.1,0.0.0.0,0.0.0.0,MPLS,,,snmpv1,vsys1,VPN,trust,tunnel.2001,ethernet1/2.900,LogToPanorama,2022/05/16 14:25:57,76592,1,58824,161,0,0,0x4019,udp,allow,1690,785,905,18,2022/05/16 14:25:25,1,any,0,578843949,0x8000000000000000,10.0.0.0-10.255.255.255,10.0.0.0-10.255.255.255,0,9,9,aged-out,29,3090,3092,0,,FIREWALLNAME,from-policy,,,0,,0,,N/A,0,0,0,0,,0,0,,,,,,,

This is currenlty in my syslog file.

$template DynaTrafficLog,"/palogs/%FROMHOST-IP%/%HOSTNAME%_traffic_%$YEAR%_%$MONTH%_%$DAY%_last_calendar_day.csv"
*.* -?DynaTrafficLog



This stores the files in /palogs/IP-address/panorama_date_.csv

All traffic logs will be in the same file. I want seperate logs based on FIREWALLNAME (column 53 in the log line) this can be different values.
I could do this using if msg contains "FIREWALLNAME" but this is not really dynamic and hard to keep up with.
Can i do this using template?

Any help on this would be appreciated.

---

