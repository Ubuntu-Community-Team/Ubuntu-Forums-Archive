---
title: "ntpd broadcasts"
date: 2007-07-04
forum: General Help
---

### Post by salud on 2007-07-04
Hi all

I am trying to run a ntp client that woul'd listen to ntp broadcasts, but I don'n want to enable any authentication. I tried to use this simple config file: 

disable auth
broadcastclient

and then I run this command:

ntpd -c (path_to_config_file)/ntp.conf -d  -n

After running this command I get this output

root@host:# ./ntpd -c (path_to_config_file)/ntp.conf -d -n 
ntpd 4.2.4p2@1.1495-o Fri Jun 29 09:33:45 UTC 2007 (1)
addto_syslog: precision = 1.000 usec
addto_syslog: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
addto_syslog: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
addto_syslog: Listening on interface #1 wildcard, ::#123 Disabled
addto_syslog: Listening on interface #2 lo, ::1#123 Enabled
addto_syslog: Listening on interface #3 eth0, fff:fff:208:hff:ffff:ffff#123 Enabled
addto_syslog: Listening on interface #4 lo, 127.0.0.1#123 Enabled
addto_syslog: Listening on interface #5 eth0, (my_IP)#123 Enabled
local_clock: time 0 offset 0.000000 freq 0.000 state 0
addto_syslog: kernel time sync status 0040
addto_syslog: io_setbclient: Opened broadcast client on interface #5 eth0, socket: 22
io_setbclient: Opened broadcast clients
local_clock: time 0 offset 0.000000 freq 0.000 state 1
report_event: system event 'event_restart' (0x01) status 'sync_alarm, sync_unspec, 1 event, event_unspec' (0xc010)
auth_agekeys: at 1 keys 1 expired 0
timer: refresh ts 0
timer: interface update
receive: at 56 (my_IP)<-(server_IP) mode 5 code 6 auth 0
auth_agekeys: at 60 keys 1 expired 0
receive: at 119 (my_IP)<-(server_IP) mode 5 code 6 auth 0
auth_agekeys: at 120 keys 1 expired 0
addto_syslog: ntpd exiting on signal 2
(ctrl c)
root@host:#

The problem is that the client isn't adjusting time even if it's obvious that it catches the broadcasts. Both server and client are running on Ubuntu 7.04.


Thanks
Andrej

---

