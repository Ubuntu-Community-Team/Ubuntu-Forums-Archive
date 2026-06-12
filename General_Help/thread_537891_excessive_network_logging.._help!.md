---
title: "excessive network logging.. help!"
date: 2007-08-29
forum: General Help
---

### Post by MustNotSleep on 2007-08-29
ever since i installed Ubuntu i noticed my /var/log/messages file to be logging repeated messages over short periods of time..  here's a snippet:

```
Aug 29 00:58:54 ivant43 syslogd 1.4.1#20ubuntu4: restart.
Aug 29 01:02:00 ivant43 kernel: [ 7357.664000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:07:01 ivant43 kernel: [ 7657.692000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:08:01 ivant43 kernel: [ 7717.720000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Aug 29 01:12:01 ivant43 kernel: [ 7957.752000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:17:07 ivant43 kernel: [ 8263.760000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:20:07 ivant43 kernel: [ 8443.764000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Aug 29 01:22:07 ivant43 kernel: [ 8563.800000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:27:07 ivant43 kernel: [ 8863.828000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:32:13 ivant43 kernel: [ 9169.840000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Aug 29 01:32:13 ivant43 kernel: [ 9169.840000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:37:13 ivant43 kernel: [ 9469.840000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:42:13 ivant43 kernel: [ 9769.848000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:44:19 ivant43 kernel: [ 9895.876000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Aug 29 01:47:19 ivant43 kernel: [10075.888000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:52:19 ivant43 kernel: [10375.892000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 01:56:19 ivant43 kernel: [10615.892000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
Aug 29 01:57:19 ivant43 kernel: [10675.892000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 02:02:25 ivant43 kernel: [10981.944000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 02:07:25 ivant43 kernel: [11282.044000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 02:08:25 ivant43 kernel: [11342.056000] Unknown OutputIN= OUT=eth1 SRC=169.254.8.173 DST=169.254.255.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
... repeated hundreds of times ...
```
apparently the culprit is eth1 (which is strange since my T43 laptop only has one Ethernet interface, eth0).. upon looking for further info i realized this was an [Avahi](http://avahi.org/) interface, and the IPs in the log belong to [IANA](http://www.dnsstuff.com/tools/whois.ch?ip=169.254.8.173).. i'm thinking this has something to do with the wireless lookup, but it seems to happen even when i disable Wireless by right-clicking on the NetworkManager Applet.. :confused:

so today i go to check it out again, and now another type of message is logged in huge amounts:
```
Aug 29 12:21:21 ivant43 kernel: [12668.184000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28269 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:22 ivant43 kernel: [12668.932000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28276 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:22 ivant43 kernel: [12668.932000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28277 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:23 ivant43 kernel: [12669.684000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28289 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:23 ivant43 kernel: [12669.684000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28290 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:23 ivant43 kernel: [12670.432000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28300 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:23 ivant43 kernel: [12670.432000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28301 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:24 ivant43 kernel: [12671.184000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28307 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:24 ivant43 kernel: [12671.184000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28308 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:25 ivant43 kernel: [12671.932000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28318 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:25 ivant43 kernel: [12671.932000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28319 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:26 ivant43 kernel: [12672.684000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28329 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:26 ivant43 kernel: [12672.684000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28330 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:27 ivant43 kernel: [12673.432000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28343 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:27 ivant43 kernel: [12673.432000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28344 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:27 ivant43 kernel: [12674.184000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28351 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:27 ivant43 kernel: [12674.184000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28352 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:28 ivant43 kernel: [12674.932000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28360 PROTO=UDP SPT=137 DPT=137 LEN=58 
Aug 29 12:21:28 ivant43 kernel: [12674.932000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:37:14:a5:08:00 SRC=10.0.0.2 DST=10.0.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=28361 PROTO=UDP SPT=137 DPT=137 LEN=58
... repeated every second it seems...
```
this last one is even more frequent than the previous message.. apparently 10.0.0.2 is a server here at work running Windows 2000 Server.. my LAN IP is 10.0.0.190 and **i'm not using DHCP, my IP is statically assigned**.. i found out that port 137 is used for/by Samba, so i tried running [FONT="Courier New"]sudo /etc/init.d/samba stop[/FONT] but it's still logging the message..

needless to say, this is putting a hit on my HD and CPU.. not in critical terms, but i certainly don't idle at 0% anymore.. and worst of all, the file is growing larger by the second.. so far it's at 8MB, up from 5MB from a few mins ago..

i'll see what i can find with the sysadmins here, but i wanted to know what you guys thought both cases could be, and if it's something i could fix on my end, or if not, what i can do to stop the excessive logging.. i'll turn off the machine for now, and see if it continues happening later..

thanks in advance!

---

