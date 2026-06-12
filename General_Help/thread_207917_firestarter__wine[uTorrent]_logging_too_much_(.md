---
title: "firestarter / wine[uTorrent] logging too much :("
date: 2006-07-02
forum: General Help
---

### Post by citizenr on 2006-07-02
$cat /var/log/messages.0
....
Jul  2 23:35:42 rasz-desktop kernel: [17186109.572000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=124.29.51.83 DST=82.210.134.82 LEN=126 TOS=0x00 PREC=0x00 TTL=111 ID=13844 PROTO=UDP SPT=15249 DPT=31618 LEN=106
Jul  2 23:35:45 rasz-desktop kernel: [17186112.344000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=75.22.224.120 DST=82.210.134.82 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=2391 DF PROTO=TCP SPT=3002 DPT=31618 WINDOW=58944 RES=0x00 SYN URGP=0
Jul  2 23:35:48 rasz-desktop kernel: [17186114.988000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=75.22.224.120 DST=82.210.134.82 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=2625 DF PROTO=TCP SPT=3002 DPT=31618 WINDOW=58944 RES=0x00 SYN URGP=0
Jul  2 23:35:54 rasz-desktop kernel: [17186121.008000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=75.22.224.120 DST=82.210.134.82 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=3119 DF PROTO=TCP SPT=3002 DPT=31618 WINDOW=58944 RES=0x00 SYN URGP=0
Jul  2 23:36:08 rasz-desktop kernel: [17186135.208000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=221.226.255.189 DST=82.210.134.82 LEN=90 TOS=0x00 PREC=0x00 TTL=113 ID=33722 PROTO=UDP SPT=12570 DPT=25827 LEN=70
Jul  2 23:36:24 rasz-desktop kernel: [17186151.540000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=121.70.174.185 DST=82.210.134.82 LEN=90 TOS=0x00 PREC=0x00 TTL=103 ID=17718 PROTO=UDP SPT=10515 DPT=31618 LEN=70

and so on, same in kern.log syslog. This is quasi ok, i get ~5-10 MB daily, but the next one is terrible.
$cat /var/log/debug.0
...
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625690 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625691 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625692 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625693 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625694 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625695 on hdc5

and so on

yesterday logs reached 1.2GB filling my / completely.

WHY is wine logging this and how to stop it? I can generate one gig just by telling uTorrent to recheck big file (lots of file reads = TONS of logs).
Winehq.org is very unfriendly :(, no web forum, only mailing list :(
another wine problem i have is here 
[http://www.ubuntuforums.org/showthread.php?t=182212](http://www.ubuntuforums.org/showthread.php?t=182212)

---

### Post by Kilz on 2006-07-02
[QUOTE=citizenr]$cat /var/log/messages.0
....
Jul  2 23:35:42 rasz-desktop kernel: [17186109.572000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=124.29.51.83 DST=82.210.134.82 LEN=126 TOS=0x00 PREC=0x00 TTL=111 ID=13844 PROTO=UDP SPT=15249 DPT=31618 LEN=106
Jul  2 23:35:45 rasz-desktop kernel: [17186112.344000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=75.22.224.120 DST=82.210.134.82 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=2391 DF PROTO=TCP SPT=3002 DPT=31618 WINDOW=58944 RES=0x00 SYN URGP=0
Jul  2 23:35:48 rasz-desktop kernel: [17186114.988000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=75.22.224.120 DST=82.210.134.82 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=2625 DF PROTO=TCP SPT=3002 DPT=31618 WINDOW=58944 RES=0x00 SYN URGP=0
Jul  2 23:35:54 rasz-desktop kernel: [17186121.008000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=75.22.224.120 DST=82.210.134.82 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=3119 DF PROTO=TCP SPT=3002 DPT=31618 WINDOW=58944 RES=0x00 SYN URGP=0
Jul  2 23:36:08 rasz-desktop kernel: [17186135.208000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=221.226.255.189 DST=82.210.134.82 LEN=90 TOS=0x00 PREC=0x00 TTL=113 ID=33722 PROTO=UDP SPT=12570 DPT=25827 LEN=70
Jul  2 23:36:24 rasz-desktop kernel: [17186151.540000] Inbound IN=eth0 OUT= MAC=00:00:b4:94:b7:af:00:14:f1:1b:4f:70:08:00 SRC=121.70.174.185 DST=82.210.134.82 LEN=90 TOS=0x00 PREC=0x00 TTL=103 ID=17718 PROTO=UDP SPT=10515 DPT=31618 LEN=70

and so on, same in kern.log syslog. This is quasi ok, i get ~5-10 MB daily, but the next one is terrible.
$cat /var/log/debug.0
...
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625690 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625691 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625692 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625693 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625694 on hdc5
Jul  2 06:21:40 rasz-desktop kernel: [17180038.448000] utorrent.exe(4673): READ block 82625695 on hdc5

and so on

yesterday logs reached 1.2GB filling my / completely.

WHY is wine logging this and how to stop it? I can generate one gig just by telling uTorrent to recheck big file (lots of file reads = TONS of logs).
Winehq.org is very unfriendly :(, no web forum, only mailing list :(
another wine problem i have is here 
[http://www.ubuntuforums.org/showthread.php?t=182212](http://www.ubuntuforums.org/showthread.php?t=182212)[/QUOTE]

Applications run under wine do not run the best. Wine isnt perfect. You may be better off using a native bit torrent program. Azureus and bittornado-gui are pretty good if you want to try them.

---

### Post by citizenr on 2006-07-08
bump
firestarter - i edited manually /etc/firestarted config fire and changed ALL to NONe , no more stupid logs 

as of utorrent still looking what dumps this shit to my logs :(

---

