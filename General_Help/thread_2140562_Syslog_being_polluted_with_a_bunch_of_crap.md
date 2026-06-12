---
title: "Syslog being polluted with a bunch of crap"
date: 2013-04-30
forum: General Help
---

### Post by Stonecold1995 on 2013-04-30
UFW is polluting syslog with a huge number of blocked IP addresses.  I run KTorrent, so I'm pretty sure that's what it's coming from, but KTorrent works, and UFW shouldn't be blocking it.

That, and a bunch of "Package power limit notification"s.

How do I stop UFW from blocking useless sh*t, and how do I get my computer to stfu about power limits??

```
[241432.772817] CPU7: Package power limit notification (total events = 79301)
[241432.772821] CPU6: Package power limit notification (total events = 79302)
[241432.772823] CPU5: Package power limit notification (total events = 79301)
[241432.772825] CPU2: Package power limit notification (total events = 79302)
[241432.772827] CPU3: Package power limit notification (total events = 79301)
[241432.772829] CPU0: Package power limit notification (total events = 79302)
[241432.772831] CPU4: Package power limit notification (total events = 79302)
[241432.772833] CPU1: Package power limit notification (total events = 79301)
[241432.784784] CPU7: Package power limit normal
[241432.784785] CPU3: Package power limit normal
[241432.784787] CPU5: Package power limit normal
[241432.784789] CPU2: Package power limit normal
[241432.784791] CPU1: Package power limit normal
[241432.784792] CPU6: Package power limit normal
[241432.784794] CPU0: Package power limit normal
[241432.784795] CPU4: Package power limit normal
[241438.170310] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=88.17.65.177 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=239 ID=34075 PROTO=TCP SPT=45804 DPT=34124 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241458.285155] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=52731 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241478.810647] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=57626 DPT=48205 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241498.946515] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=53516 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241519.536529] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=53884 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241541.762014] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=49.132.38.10 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=46131 DF PROTO=TCP SPT=51398 DPT=55383 WINDOW=0 RES=0x00 RST URGP=0 
[241564.888591] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=54761 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241578.489757] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=39496 DPT=60052 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241597.798856] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=55246 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241617.806958] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=75.93.224.151 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=TCP SPT=40883 DPT=58998 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241640.289537] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=85.109.160.152 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=TCP SPT=15982 DPT=48105 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241664.307386] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=56342 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241677.775141] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=56562 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241700.528431] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=56950 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241725.318294] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=37.59.6.143 DST=10.8.0.34 LEN=134 TOS=0x00 PREC=0x00 TTL=57 ID=62777 DF PROTO=TCP SPT=51413 DPT=51249 WINDOW=122 RES=0x00 ACK PSH URGP=0 
[241727.516516] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=121.240.72.165 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=244 ID=33738 PROTO=TCP SPT=17763 DPT=50815 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241737.669366] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=80.203.123.27 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=61207 DF PROTO=TCP SPT=6881 DPT=43788 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241752.300690] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=37.59.6.143 DST=10.8.0.34 LEN=134 TOS=0x00 PREC=0x00 TTL=57 ID=62778 DF PROTO=TCP SPT=51413 DPT=51249 WINDOW=122 RES=0x00 ACK PSH URGP=0 
[241757.730967] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=58112 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241784.206292] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=60.48.97.177 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=247 ID=43687 PROTO=TCP SPT=55555 DPT=52232 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241803.442467] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=59102 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241806.286171] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=37.59.6.143 DST=10.8.0.34 LEN=134 TOS=0x00 PREC=0x00 TTL=57 ID=62779 DF PROTO=TCP SPT=51413 DPT=51249 WINDOW=122 RES=0x00 ACK PSH URGP=0 
[241811.086110] CPU5: Package power limit notification (total events = 79315)
[241811.086113] CPU7: Package power limit notification (total events = 79315)
[241811.086115] CPU2: Package power limit notification (total events = 79316)
[241811.086117] CPU1: Package power limit notification (total events = 79315)
[241811.086119] CPU3: Package power limit notification (total events = 79315)
[241811.086121] CPU6: Package power limit notification (total events = 79316)
[241811.086124] CPU0: Package power limit notification (total events = 79316)
[241811.086125] CPU4: Package power limit notification (total events = 79316)
[241811.099150] CPU4: Package power limit normal
[241811.099152] CPU6: Package power limit normal
[241811.099154] CPU5: Package power limit normal
[241811.099155] CPU2: Package power limit normal
[241811.099157] CPU3: Package power limit normal
[241811.099158] CPU0: Package power limit normal
[241811.099160] CPU1: Package power limit normal
[241811.099161] CPU7: Package power limit normal
[241819.632653] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=59465 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241841.371318] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=119.93.97.222 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=234 ID=6495 PROTO=TCP SPT=41097 DPT=59953 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241860.444110] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=111.226.202.151 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=42 ID=25251 DF PROTO=TCP SPT=11016 DPT=60869 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241877.634036] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=186.193.223.34 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=17571 DPT=59116 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241897.264595] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=33243 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241917.230448] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=76.226.58.8 DST=10.8.0.34 LEN=63 TOS=0x00 PREC=0x00 TTL=238 ID=59046 DF PROTO=TCP SPT=11689 DPT=43837 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241937.363894] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=184.75.221.106 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=TCP SPT=27424 DPT=60096 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241962.473793] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=35045 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241977.693510] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=35309 WINDOW=0 RES=0x00 ACK RST URGP=0 
[241998.404461] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=58.34.5.8 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=TCP SPT=16199 DPT=44278 WINDOW=0 RES=0x00 ACK RST URGP=0 
[242017.985410] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=187.232.125.186 DST=10.8.0.34 LEN=63 TOS=0x00 PREC=0x00 TTL=243 ID=20883 DF PROTO=TCP SPT=48513 DPT=58199 WINDOW=0 RES=0x00 ACK RST URGP=0 
[242051.394194] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=180.191.6.78 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=3920 PROTO=TCP SPT=36498 DPT=56769 WINDOW=0 RES=0x00 ACK RST URGP=0 
[242064.820435] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=72.227.168.224 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=4944 PROTO=TCP SPT=29307 DPT=55519 WINDOW=0 RES=0x00 ACK RST URGP=0 
[242077.301670] [UFW BLOCK] IN=tun0 OUT= MAC= SRC=95.211.10.3 DST=10.8.0.34 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=6881 DPT=37080 WINDOW=0 RES=0x00 ACK RST URGP=0
```

This kind of thing is repeated CONSTANTLY, so if I use sed to remove every line with "UFW BLOCK" and "CPU" I get a handful of lines, even in all of my syslog files.

---

### Post by Stonecold1995 on 2013-05-02
bump

---

### Post by Stonecold1995 on 2013-05-28
bump

---

### Post by HiImTye on 2013-05-28
set your torrent client to listen to a set port (you should anyway), and then
```
sudo sed -ie 's|IPV6=yes|IPV6=no|' /etc/default/ufw
sudo ufw allow #/tcp
```
replacing # with the port
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by btindie on 2013-05-28
From *man ufw*
> logging on|off|LEVEL              toggle logging. Logged packets use the LOG_KERN syslog facility. Systems configured for rsyslog support  may  also
              log  to  /var/log/ufw.log.  Specifying  a LEVEL turns logging on for the specified LEVEL. The default log level is
              'low'.  See LOGGING for details.


By default UFW syslog messages will go to all files that are configured for LOG_KERN. You can prevent this by uncommenting the last line in */etc/rsyslog.d/20-ufw.conf* so it looks like
```
# Log kernel generated UFW log messages to file:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
& ~

```

and restarting rsyslog.

---

### Post by Stonecold1995 on 2013-05-31
> **HiImTye said:**
> set your torrent client to listen to a set port (you should anyway), and then
```
sudo sed -ie 's|IPV6=yes|IPV6=no|' /etc/default/ufw
sudo ufw allow #/tcp
```
replacing # with the port

KTorrent shows that it has a port set (it just says "port"), a separate port for UDP trackers, and a third port for DHT.  Which do I set it to?  All of them?

---

### Post by HiImTye on 2013-05-31
make sure they are set so they won't change and then you can add them all to the same rule, so long as they are all TCP
```
sudo ufw allow #,#,#/tcp
# -- or a range --
sudo ufw allow #:#/tcp
# -- or mixed --
sudo ufw allow #:#,#,#/tcp
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Stonecold1995 on 2013-06-11
And how do I prevent the power package limit notifications?

---

### Post by HiImTye on 2013-06-11
that's a heat warning from your CPU. it could be you need better cooling/ventilation, or you could have the syslog ignore them if your temperatures are fine. you may need to simply clean your fan(s) & heatsink(s)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Stonecold1995 on 2013-06-11
> **HiImTye said:**
> that's a heat warning from your CPU. it could be you need better cooling/ventilation, or you could have the syslog ignore them if your temperatures are fine. you may need to simply clean your fan(s) & heatsink(s)

I am running Folding@home and several other (unrelated) programs that use up a large amount of CPU, so I am almost always at 100% load.  My computer is a laptop, but it's a gaming laptop and has very good ventillation as well as a cooling pad, but I think there's no getting around the warnings when my CPU stays at an average of 97 degrees Celsius all the time.

How do I have syslog ignore them, or only display them if the temperature goes *really* high or critical?

---

### Post by HiImTye on 2013-06-12
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try adding something like
```
:message,contains,"Package power" ~
```before the syslog line in
```
/etc/rsyslog.d/50-default.conf
```
so that it reads
```
...
:message,contains,"Package power" ~
*.*,auth,authpriv.none -/var/log/syslog
...
```

---

### Post by Stonecold1995 on 2013-06-28
> **HiImTye said:**
> try adding something like
```
:message,contains,"Package power" ~
```before the syslog line in
```
/etc/rsyslog.d/50-default.conf
```
so that it reads
```
...
:message,contains,"Package power" ~
*.*,auth,authpriv.none -/var/log/syslog
...
```
So is this correct?

```
#  Default rules for rsyslog.#
#                       For more information see rsyslog.conf(5) and /etc/rsyslog.conf


#
# First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
[B]:message,contains,"temperature/speed normal" ~
:message,contains,"temperature above threshold, cpu clock throttled" ~[/B]
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
#daemon.*                       -/var/log/daemon.log
kern.*                          -/var/log/kern.log
#lpr.*                          -/var/log/lpr.log
mail.*                          -/var/log/mail.log
#user.*                         -/var/log/user.log

...
```

---

### Post by HiImTye on 2013-06-29
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
that doesn't look like the errors you showed, but if those are there now, sure

---

### Post by Stonecold1995 on 2013-06-30
> **HiImTye said:**
> that doesn't look like the errors you showed, but if those are there now, sure
Well, it looks like this now.
```
[5566567.885525] CPU3: Package temperature above threshold, cpu clock throttled (total events = 620382512)[5566567.886519] CPU3: Package temperature/speed normal
[5566567.973571] CPU4: Package temperature/speed normal
[5566567.973574] CPU5: Package temperature/speed normal
[5566567.987588] CPU0: Package temperature above threshold, cpu clock throttled (total events = 620383104)
[5566567.987590] CPU7: Package temperature above threshold, cpu clock throttled (total events = 620382565)
[5566567.988584] CPU0: Package temperature/speed normal
[5566567.988586] CPU7: Package temperature/speed normal
[5566568.009617] CPU1: Package temperature/speed normal
[5566568.145690] CPU6: Package temperature above threshold, cpu clock throttled (total events = 620382073)
[5566568.145692] CPU2: Package temperature above threshold, cpu clock throttled (total events = 620382629)
[5566568.146684] CPU6: Package temperature/speed normal
[5566568.146686] CPU2: Package temperature/speed normal
[5566623.778142] CPU3: Core temperature above threshold, cpu clock throttled (total events = 224736027)
[5566623.778144] CPU7: Core temperature above threshold, cpu clock throttled (total events = 224736017)
[5566623.779145] CPU3: Core temperature/speed normal
[5566623.779146] CPU7: Core temperature/speed normal
```

Also, after saving the file, when will the effect start?  Do I have to restart rsyslogd?  Reboot?

---

