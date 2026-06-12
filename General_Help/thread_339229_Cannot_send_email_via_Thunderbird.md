---
title: "Cannot send email via Thunderbird"
date: 2007-01-15
forum: General Help
---

### Post by khyd on 2007-01-15
Hi all,

I have been using Linux for a week now (switch from Windows XP).
Everything works great, I manage to find similar programs that the one I used to use on Windows.

This past weekend I had 2 problems:

[INDENT]- unable to see my USB hard disk, whereas it used to work, so I did reinstall everything link to mounting a volume and it work out afterwards :p It still does not work plugging the USBDisk once the computer is started, but I don't really care about that (it is just to inform you of the problem, I do not need any fix for that).[/INDENT]

[INDENT]- unable to send emails using Thunderbird, whereas I can receive no problem, I can ping my SMTP server, I can Telnet it too. I did try to put authentication on the SMTP without any result. I tried also different SMTP servers without success. I did try to send a simple text email... still nothing good. Whereas everything was working on Windows with the same settings :confused: I do not know what to do, can anyone help?[/INDENT]

Reading in different forums tells me that problem exist with some other people.

Since it was my first time on Linux, I did install and uninstall a lot of programs but I did not touch to anything too sensitive (I hope so).

Please, help me figure that thing out, I hoping to switch a lot of computer to Ubuntu once I'll understand it more.

---

### Post by mvaniersel on 2007-01-15
Were you using thunderbird on windows too? 

The nice thing about thunderbird is that you can copy over your old profile directory from a windows machine and a linux machine and all your old mail and settings will be there. (In fact, while dual booting, I have thunderbird set up so that both on windows and on linux it uses the exact same profile)

In other words, if you can get it to work on windows, you should simply be able to copy your profile to linux and it should work there too.

---

### Post by marianom on 2007-01-15
do you get any useful error message that can help to trace the problem?

---

### Post by khyd on 2007-01-16
I wish I had an error message, but no.
It just tells me, after 2 minutes, to check my SMTP settings which are good.

The thing I have not tried is to uninstall thunderbird, delete my profile, then install thunderbird.

I would like to make logs of the SMTP exchange but I do not know where to activate this, can some one tell me?

---

### Post by khyd on 2007-01-18
Hi,

I manage to make some traces using WireShark.

It seems like there is something no allowing me to access the port 25. Even if I can ping and telnet it ](*,) .

Thank you to guide me guys, I really want to have this email system work.

Here are the long trace:

No.     Time        Source                Destination           Protocol Info
      1 0.000000    192.168.77.2          82.211.81.145         NTP      NTP

Frame 1 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 82.211.81.145 (82.211.81.145)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
      2 0.002215    192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

Frame 2 (139 bytes on wire, 139 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
      3 0.002278    192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 3 (167 bytes on wire, 167 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
      4 0.651270    82.211.81.145         192.168.77.2          NTP      NTP

Frame 4 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 82.211.81.145 (82.211.81.145), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
      5 3.998788    192.168.77.2          132.246.168.164       NTP      NTP

Frame 5 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 132.246.168.164 (132.246.168.164)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
      6 4.000946    192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

Frame 6 (141 bytes on wire, 141 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
      7 4.001014    192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 7 (169 bytes on wire, 169 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
      8 4.190401    132.246.168.164       192.168.77.2          NTP      NTP

Frame 8 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 132.246.168.164 (132.246.168.164), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
      9 62.997978   192.168.77.2          82.211.81.145         NTP      NTP

Frame 9 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 82.211.81.145 (82.211.81.145)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     10 63.000293   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

Frame 10 (139 bytes on wire, 139 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
     11 63.000360   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 11 (167 bytes on wire, 167 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     12 63.611911   82.211.81.145         192.168.77.2          NTP      NTP

Frame 12 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 82.211.81.145 (82.211.81.145), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     13 67.996483   AcctonTe_07:73:8e     Bewan_37:14:26        ARP      Who has 192.168.77.1?  Tell 192.168.77.2

Frame 13 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     14 67.996751   Bewan_37:14:26        AcctonTe_07:73:8e     ARP      192.168.77.1 is at 00:0c:c3:37:14:26

Frame 14 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     15 68.779618   192.168.77.2          209.94.64.1           DNS      Standard query AAAA amigo.net

Frame 15 (69 bytes on wire, 69 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.1 (209.94.64.1)
User Datagram Protocol, Src Port: 1030 (1030), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     16 68.781826   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.1 PROTO=UDP SPT=1030 DPT=53 

Frame 16 (137 bytes on wire, 137 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.1 PROTO=UDP SPT=1030 DPT=53 

No.     Time        Source                Destination           Protocol Info
     17 68.781860   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 17 (165 bytes on wire, 165 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     18 68.801349   209.94.64.1           192.168.77.2          DNS      Standard query response

Frame 18 (120 bytes on wire, 120 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 209.94.64.1 (209.94.64.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: domain (53), Dst Port: 1030 (1030)
Domain Name System (response)

No.     Time        Source                Destination           Protocol Info
     19 70.004049   192.168.77.2          132.246.168.164       NTP      NTP

Frame 19 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 132.246.168.164 (132.246.168.164)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     20 70.006160   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

Frame 20 (141 bytes on wire, 141 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
     21 70.006215   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 21 (169 bytes on wire, 169 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     22 70.119703   132.246.168.164       192.168.77.2          NTP      NTP

Frame 22 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 132.246.168.164 (132.246.168.164), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     23 70.347231   192.168.77.2          209.94.64.1           DNS      Standard query AAAA amigo.net

Frame 23 (69 bytes on wire, 69 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.1 (209.94.64.1)
User Datagram Protocol, Src Port: 1030 (1030), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     24 70.360810   209.94.64.1           192.168.77.2          DNS      Standard query response

Frame 24 (120 bytes on wire, 120 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 209.94.64.1 (209.94.64.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: domain (53), Dst Port: 1030 (1030)
Domain Name System (response)

No.     Time        Source                Destination           Protocol Info
     25 70.363905   192.168.77.2          209.94.64.1           DNS      Standard query A amigo.net

Frame 25 (69 bytes on wire, 69 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.1 (209.94.64.1)
User Datagram Protocol, Src Port: 1030 (1030), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
     26 70.373000   209.94.64.1           192.168.77.2          DNS      Standard query response A 209.94.64.11

Frame 26 (153 bytes on wire, 153 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 209.94.64.1 (209.94.64.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: domain (53), Dst Port: 1030 (1030)
Domain Name System (response)

No.     Time        Source                Destination           Protocol Info
     27 70.396020   192.168.77.2          209.94.64.11          TCP      2685 > smtp [SYN] Seq=0 Len=0 MSS=1460 TSV=800 TSER=0 WS=2

Frame 27 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.11 (209.94.64.11)
Transmission Control Protocol, Src Port: 2685 (2685), Dst Port: smtp (25), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     28 70.398210   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

Frame 28 (138 bytes on wire, 138 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

No.     Time        Source                Destination           Protocol Info
     29 70.398286   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 29 (166 bytes on wire, 166 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     30 73.394973   192.168.77.2          209.94.64.11          TCP      2685 > smtp [SYN] Seq=0 Len=0 MSS=1460 TSV=1550 TSER=0 WS=2

Frame 30 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.11 (209.94.64.11)
Transmission Control Protocol, Src Port: 2685 (2685), Dst Port: smtp (25), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     31 73.396924   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

Frame 31 (138 bytes on wire, 138 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

No.     Time        Source                Destination           Protocol Info
     32 73.396990   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 32 (166 bytes on wire, 166 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     33 79.393248   192.168.77.2          209.94.64.11          TCP      2685 > smtp [SYN] Seq=0 Len=0 MSS=1460 TSV=3050 TSER=0 WS=2

Frame 33 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.11 (209.94.64.11)
Transmission Control Protocol, Src Port: 2685 (2685), Dst Port: smtp (25), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     34 79.395393   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

Frame 34 (138 bytes on wire, 138 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

No.     Time        Source                Destination           Protocol Info
     35 79.395458   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 35 (166 bytes on wire, 166 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     36 91.389855   192.168.77.2          209.94.64.11          TCP      2685 > smtp [SYN] Seq=0 Len=0 MSS=1460 TSV=6050 TSER=0 WS=2

Frame 36 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.11 (209.94.64.11)
Transmission Control Protocol, Src Port: 2685 (2685), Dst Port: smtp (25), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     37 91.392002   192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

Frame 37 (138 bytes on wire, 138 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

No.     Time        Source                Destination           Protocol Info
     38 91.392068   192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 38 (166 bytes on wire, 166 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     39 115.383043  192.168.77.2          209.94.64.11          TCP      2685 > smtp [SYN] Seq=0 Len=0 MSS=1460 TSV=12050 TSER=0 WS=2

Frame 39 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.11 (209.94.64.11)
Transmission Control Protocol, Src Port: 2685 (2685), Dst Port: smtp (25), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     40 115.385241  192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

Frame 40 (138 bytes on wire, 138 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

No.     Time        Source                Destination           Protocol Info
     41 115.385319  192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 41 (166 bytes on wire, 166 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     42 120.381604  AcctonTe_07:73:8e     Bewan_37:14:26        ARP      Who has 192.168.77.1?  Tell 192.168.77.2

Frame 42 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     43 120.381918  Bewan_37:14:26        AcctonTe_07:73:8e     ARP      192.168.77.1 is at 00:0c:c3:37:14:26

Frame 43 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     44 128.999411  192.168.77.2          82.211.81.145         NTP      NTP

Frame 44 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 82.211.81.145 (82.211.81.145)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     45 129.001687  192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

Frame 45 (139 bytes on wire, 139 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
     46 129.001755  192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 46 (167 bytes on wire, 167 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     47 129.268999  82.211.81.145         192.168.77.2          NTP      NTP

Frame 47 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 82.211.81.145 (82.211.81.145), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     48 133.998103  192.168.77.2          132.246.168.164       NTP      NTP

Frame 48 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 132.246.168.164 (132.246.168.164)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     49 134.000569  192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

Frame 49 (141 bytes on wire, 141 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
     50 134.000643  192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 50 (169 bytes on wire, 169 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     51 134.326976  132.246.168.164       192.168.77.2          NTP      NTP

Frame 51 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 132.246.168.164 (132.246.168.164), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     52 163.369407  192.168.77.2          209.94.64.11          TCP      2685 > smtp [SYN] Seq=0 Len=0 MSS=1460 TSV=24050 TSER=0 WS=2

Frame 52 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 209.94.64.11 (209.94.64.11)
Transmission Control Protocol, Src Port: 2685 (2685), Dst Port: smtp (25), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     53 163.371703  192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

Frame 53 (138 bytes on wire, 138 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=209.94.64.11 PROTO=TCP SPT=2685 DPT=25 

No.     Time        Source                Destination           Protocol Info
     54 163.371769  192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 54 (166 bytes on wire, 166 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     55 168.367991  AcctonTe_07:73:8e     Bewan_37:14:26        ARP      Who has 192.168.77.1?  Tell 192.168.77.2

Frame 55 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     56 168.368304  Bewan_37:14:26        AcctonTe_07:73:8e     ARP      192.168.77.1 is at 00:0c:c3:37:14:26

Frame 56 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
     57 194.000791  192.168.77.2          82.211.81.145         NTP      NTP

Frame 57 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 82.211.81.145 (82.211.81.145)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     58 194.003079  192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

Frame 58 (139 bytes on wire, 139 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=82.211.81.145 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
     59 194.003144  192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 59 (167 bytes on wire, 167 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     60 194.533655  82.211.81.145         192.168.77.2          NTP      NTP

Frame 60 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 82.211.81.145 (82.211.81.145), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     61 197.999640  192.168.77.2          132.246.168.164       NTP      NTP

Frame 61 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 132.246.168.164 (132.246.168.164)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     62 198.001802  192.168.77.1          192.168.77.2          Syslog   USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

Frame 62 (141 bytes on wire, 141 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 192.168.77.1 (192.168.77.1), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: 1026 (1026), Dst Port: syslog (514)
Syslog message: USER.WARNING: kernel: outgoing IN=lan OUT=wan SRC=192.168.77.2 DST=132.246.168.164 PROTO=UDP SPT=123 DPT=123 

No.     Time        Source                Destination           Protocol Info
     63 198.001870  192.168.77.2          192.168.77.1          ICMP     Destination unreachable (Port unreachable)

Frame 63 (169 bytes on wire, 169 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Internet Protocol, Src: 192.168.77.2 (192.168.77.2), Dst: 192.168.77.1 (192.168.77.1)
Internet Control Message Protocol

No.     Time        Source                Destination           Protocol Info
     64 198.541894  132.246.168.164       192.168.77.2          NTP      NTP

Frame 64 (90 bytes on wire, 90 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Internet Protocol, Src: 132.246.168.164 (132.246.168.164), Dst: 192.168.77.2 (192.168.77.2)
User Datagram Protocol, Src Port: ntp (123), Dst Port: ntp (123)
Network Time Protocol

No.     Time        Source                Destination           Protocol Info
     65 202.998142  AcctonTe_07:73:8e     Bewan_37:14:26        ARP      Who has 192.168.77.1?  Tell 192.168.77.2

Frame 65 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: AcctonTe_07:73:8e (00:10:b5:07:73:8e), Dst: Bewan_37:14:26 (00:0c:c3:37:14:26)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     66 202.998401  Bewan_37:14:26        AcctonTe_07:73:8e     ARP      192.168.77.1 is at 00:0c:c3:37:14:26

Frame 66 (60 bytes on wire, 60 bytes captured)
Ethernet II, Src: Bewan_37:14:26 (00:0c:c3:37:14:26), Dst: AcctonTe_07:73:8e (00:10:b5:07:73:8e)
Address Resolution Protocol (reply)

---

