---
title: "log file sizes"
date: 2016-07-21
forum: General Help
---

### Post by wyndlass on 2016-07-21
i noticed that i have 3 log files over 1gb in size and was wondering i should be worried about anything besides their size.


```


kernel.log.1     3.8GB           syslog    44.4gb     syslog.1         10.6gb


```


thanx.

---

### Post by howefield on 2016-07-21
Something is very wrong for the files to be that large, so it is worth investigating as to what appears to be spamming the log files. You could open a terminal and try, eg,

```
tail -f /var/log/syslog
```

for a few seconds, Ctrl + c to end the capture. Look for repeated messages.

---

### Post by wyndlass on 2016-07-21
there are lots of entries that show ufw;


```


Jul 21 12:16:54 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62721.317859] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:28:c6:8e:7a:a6:da:08:00 SRC=216.58.216.238 DST=192.168.1.19 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=31228 PROTO=TCP SPT=443 DPT=50444 WINDOW=46286 RES=0x00 ACK URGP=0 
Jul 21 12:16:54 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62721.336454] [UFW AUDIT] IN=wlo1 OUT= MAC=ff:ff:ff:ff:ff:ff:28:c6:8e:7a:a6:da:08:00 SRC=192.168.1.1 DST=255.255.255.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32772 DPT=7423 LEN=181 
Jul 21 12:16:54 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62721.630669] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=65125 DF PROTO=TCP SPT=54920 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:54 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62721.630727] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=65125 DF PROTO=TCP SPT=54920 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:54 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62721.630768] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16136 DF PROTO=TCP SPT=9614 DPT=54920 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:54 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62721.630791] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16136 DF PROTO=TCP SPT=9614 DPT=54920 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:55 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62722.630204] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=21671 DF PROTO=TCP SPT=54922 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:55 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62722.630257] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=21671 DF PROTO=TCP SPT=54922 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:55 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62722.630297] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16280 DF PROTO=TCP SPT=9614 DPT=54922 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:55 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62722.630327] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16280 DF PROTO=TCP SPT=9614 DPT=54922 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:56 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62723.629595] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=29062 DF PROTO=TCP SPT=54924 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:56 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62723.629637] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=29062 DF PROTO=TCP SPT=54924 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:56 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62723.629671] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16424 DF PROTO=TCP SPT=9614 DPT=54924 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:56 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62723.629691] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16424 DF PROTO=TCP SPT=9614 DPT=54924 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.080225] [UFW AUDIT] IN= OUT=wlo1 SRC=192.168.1.19 DST=172.217.4.238 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=42283 DF PROTO=TCP SPT=50432 DPT=443 WINDOW=237 RES=0x00 ACK URGP=0 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.081477] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:28:c6:8e:7a:a6:da:08:00 SRC=172.217.4.238 DST=192.168.1.19 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=34185 PROTO=TCP SPT=443 DPT=50432 WINDOW=46286 RES=0x00 ACK URGP=0 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.204834] [UFW AUDIT] IN=wlo1 OUT= MAC=ff:ff:ff:ff:ff:ff:28:c6:8e:7a:a6:da:08:00 SRC=192.168.1.1 DST=255.255.255.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32772 DPT=7423 LEN=181 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.629042] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=2895 DF PROTO=TCP SPT=54926 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.629081] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=2895 DF PROTO=TCP SPT=54926 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.629112] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16671 DF PROTO=TCP SPT=9614 DPT=54926 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:57 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62724.629130] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16671 DF PROTO=TCP SPT=9614 DPT=54926 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:58 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62725.628652] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15120 DF PROTO=TCP SPT=54928 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:58 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62725.628709] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15120 DF PROTO=TCP SPT=54928 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:58 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62725.628757] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16843 DF PROTO=TCP SPT=9614 DPT=54928 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:58 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62725.628794] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=16843 DF PROTO=TCP SPT=9614 DPT=54928 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:59 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62726.628200] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=30990 DF PROTO=TCP SPT=54930 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:59 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62726.628247] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=30990 DF PROTO=TCP SPT=54930 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:16:59 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62726.628285] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=17031 DF PROTO=TCP SPT=9614 DPT=54930 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:16:59 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62726.628308] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=17031 DF PROTO=TCP SPT=9614 DPT=54930 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:17:00 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62727.272553] [UFW AUDIT] IN=wlo1 OUT= MAC=ff:ff:ff:ff:ff:ff:28:c6:8e:7a:a6:da:08:00 SRC=192.168.1.1 DST=255.255.255.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32772 DPT=7423 LEN=181 
Jul 21 12:17:00 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62727.627991] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=63769 DF PROTO=TCP SPT=54932 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:17:00 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62727.628052] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=63769 DF PROTO=TCP SPT=54932 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:17:00 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62727.628093] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=17218 DF PROTO=TCP SPT=9614 DPT=54932 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:17:00 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62727.628117] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=17218 DF PROTO=TCP SPT=9614 DPT=54932 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC CRON[32014]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.626564] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=19655 DF PROTO=TCP SPT=54934 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.626619] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=19655 DF PROTO=TCP SPT=54934 DPT=9614 WINDOW=43690 RES=0x00 SYN URGP=0 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.626659] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=17396 DF PROTO=TCP SPT=9614 DPT=54934 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.626681] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=17396 DF PROTO=TCP SPT=9614 DPT=54934 WINDOW=0 RES=0x00 ACK RST URGP=0 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.701562] [UFW AUDIT] IN= OUT=wlo1 SRC=192.168.1.19 DST=209.242.224.117 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=61569 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.701578] [UFW ALLOW] IN= OUT=wlo1 SRC=192.168.1.19 DST=209.242.224.117 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=61569 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.701664] [UFW AUDIT] IN= OUT=wlo1 SRC=192.168.1.19 DST=198.211.106.151 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=64861 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.701673] [UFW ALLOW] IN= OUT=wlo1 SRC=192.168.1.19 DST=198.211.106.151 LEN=76 TOS=0x00 PREC=0xC0 TTL=64 ID=64861 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Jul 21 12:17:01 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [62728.825445] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:28:c6:8e:7a:a6:da:08:00 SRC=198.211.106.151 DST=192.168.1.19 LEN=76 TOS=0x00 PREC=0xC0 TTL=53 ID=39353 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
^C

```


i went into gufw and it's log has only 2 entries;


```


[2016-04-24 04:15:19 PM] ufw Logging: Full
[2016-04-11 01:07:37 PM] Status: Enabled


```

---

### Post by deadflowr on 2016-07-21
Lower your logging LEVEL:
from man ufw (what gufw uses):
```
LOGGING
       ufw supports multiple logging levels. ufw defaults  to  a  loglevel  of
       'low'  when  a  loglevel is not specified. Users may specify a loglevel
       with:

         ufw logging LEVEL

       LEVEL may be 'off', 'low', 'medium', 'high' and 'full'. Log levels  are
       defined as:

       off    disables ufw managed logging

       low    logs  all  blocked packets not matching the defined policy (with
              rate limiting), as well as packets matching logged rules

       medium log level low, plus all allowed packets not matching the defined
              policy,  all INVALID packets, and all new connections.  All log&#8208;
              ging is done with rate limiting.

       high   log level medium (without rate limiting), plus all packets  with
              rate limiting

       full   log level high without rate limiting

       Loglevels  above  medium  generate  a  lot  of  logging output, and may
       quickly fill up your disk. Loglevel medium may generate a lot  of  log&#8208;
       ging output on a busy system.

       Specifying 'on' simply enables logging at log level 'low' if logging is
       currently not enabled.
```
medium sounds like a good level, unless you have some reason to have logging set so high.

---

### Post by wyndlass on 2016-07-21
i set it to low. i'm guessing i can delete those 3 huge logs.

---

### Post by howefield on 2016-07-21
> **wyndlass said:**
> i set it to low. i'm guessing i can delete those 3 huge logs.

Well yes, but best to first check the other logs if you haven't already in case there is something else.

---

### Post by wyndlass on 2016-07-21
```


Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.640789] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.640892] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.640929] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.640960] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.641017] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.641033] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.641175] pci_bus 0000:01: Allocating resources
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.641196] pci_bus 0000:02: Allocating resources
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.641215] pci_bus 0000:03: Allocating resources
Jul 18 07:18:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [32192.641254] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment



```

the above is my kern.log.1 using tail and below is syslog.1



```


May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.601679] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36854 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.603286] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36855 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.603308] [UFW AUDIT] IN= OUT=wlo1 SRC=172.16.20.9 DST=74.125.159.27 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=64179 DF PROTO=TCP SPT=57128 DPT=80 WINDOW=1444 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.605912] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36856 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.606589] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36857 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.606601] [UFW AUDIT] IN= OUT=wlo1 SRC=172.16.20.9 DST=74.125.159.27 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=64180 DF PROTO=TCP SPT=57128 DPT=80 WINDOW=1444 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.607329] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36858 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.607970] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36859 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.607987] [UFW AUDIT] IN= OUT=wlo1 SRC=172.16.20.9 DST=74.125.159.27 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=64181 DF PROTO=TCP SPT=57128 DPT=80 WINDOW=1444 RES=0x00 ACK URGP=0 
May 27 13:09:18 jadaja-HP-Pavilion-g7-Notebook-PC kernel: [ 2375.608609] [UFW AUDIT] IN=wlo1 OUT= MAC=84:4b:f5:27:be:e7:00:ff:64:f9:ac:04:08:00 SRC=74.125.159.27 DST=172.16.20.9 LEN=1500 TOS=0x00 PREC=0x00 TTL=64 ID=36860 DF PROTO=TCP SPT=80 DPT=57128 WINDOW=3538 RES=0x00 ACK PSH URGP=0 



```

of course using tail again.  i tried using gedit to open up kern.log.1 but i ran out of memory and kern is the smallest of the 3.

---

### Post by wyndlass on 2016-07-24
i deleted those bloated logs, thanx for the help.

---

