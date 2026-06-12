---
title: "Printing to network printer"
date: 2007-03-01
forum: General Help
---

### Post by NeilBlanchard on 2007-03-01
Greetings,

I have a D-Link DP-301U network print server, that has an Epson Stylus 900 plugged into it (with a USB cable), and the network address is 192.168.0.10.  In the past with other Linux distros, and with Windows, this works fine.

In Ubuntu 64bit 6.10, it seems to set up properly as a network printer, but the test page never prints.  :( 

How can I troubleshoot this?

Neil

---

### Post by DagMan on 2007-03-01
can you ping the printer?  Maybe the computer can't see it.
are you sure the drivers are installed properly?

Maybe if you post what brand and model printer it is and how the network is setup, someone else who has the same machine and people who understand networking well can help out much better.

Good luck.

---

### Post by NeilBlanchard on 2007-03-02
Hello,

I pinged 192.168.0.10 successfully:

> neil@Luna4:~$ ping 192.168.0.10
PING 192.168.0.10 (192.168.0.10) 56(84) bytes of data.
64 bytes from 192.168.0.10: icmp_seq=1 ttl=255 time=8.90 ms
64 bytes from 192.168.0.10: icmp_seq=2 ttl=255 time=3.15 ms
64 bytes from 192.168.0.10: icmp_seq=3 ttl=255 time=2.76 ms
64 bytes from 192.168.0.10: icmp_seq=4 ttl=255 time=3.07 ms
64 bytes from 192.168.0.10: icmp_seq=5 ttl=255 time=2.65 ms
64 bytes from 192.168.0.10: icmp_seq=6 ttl=255 time=3.16 ms
64 bytes from 192.168.0.10: icmp_seq=7 ttl=255 time=3.13 ms
64 bytes from 192.168.0.10: icmp_seq=8 ttl=255 time=3.08 ms
64 bytes from 192.168.0.10: icmp_seq=9 ttl=255 time=2.75 ms
64 bytes from 192.168.0.10: icmp_seq=10 ttl=255 time=2.64 ms
64 bytes from 192.168.0.10: icmp_seq=11 ttl=255 time=3.01 ms
64 bytes from 192.168.0.10: icmp_seq=12 ttl=255 time=2.60 ms
64 bytes from 192.168.0.10: icmp_seq=13 ttl=255 time=3.08 ms
64 bytes from 192.168.0.10: icmp_seq=14 ttl=255 time=3.06 ms
64 bytes from 192.168.0.10: icmp_seq=15 ttl=255 time=3.10 ms
64 bytes from 192.168.0.10: icmp_seq=16 ttl=255 time=3.24 ms
64 bytes from 192.168.0.10: icmp_seq=17 ttl=255 time=2.69 ms
64 bytes from 192.168.0.10: icmp_seq=18 ttl=255 time=2.64 ms
64 bytes from 192.168.0.10: icmp_seq=19 ttl=255 time=2.78 ms
64 bytes from 192.168.0.10: icmp_seq=20 ttl=255 time=3.10 ms
64 bytes from 192.168.0.10: icmp_seq=21 ttl=255 time=3.13 ms
64 bytes from 192.168.0.10: icmp_seq=22 ttl=255 time=3.15 ms
64 bytes from 192.168.0.10: icmp_seq=23 ttl=255 time=3.22 ms
64 bytes from 192.168.0.10: icmp_seq=24 ttl=255 time=2.67 ms
64 bytes from 192.168.0.10: icmp_seq=25 ttl=255 time=3.12 ms
64 bytes from 192.168.0.10: icmp_seq=26 ttl=255 time=3.18 ms
64 bytes from 192.168.0.10: icmp_seq=27 ttl=255 time=3.05 ms
64 bytes from 192.168.0.10: icmp_seq=28 ttl=255 time=2.68 ms
64 bytes from 192.168.0.10: icmp_seq=29 ttl=255 time=3.06 ms
64 bytes from 192.168.0.10: icmp_seq=30 ttl=255 time=2.64 ms
64 bytes from 192.168.0.10: icmp_seq=31 ttl=255 time=3.14 ms
64 bytes from 192.168.0.10: icmp_seq=32 ttl=255 time=2.67 ms
64 bytes from 192.168.0.10: icmp_seq=33 ttl=255 time=2.62 ms
64 bytes from 192.168.0.10: icmp_seq=34 ttl=255 time=3.05 ms
64 bytes from 192.168.0.10: icmp_seq=35 ttl=255 time=2.99 ms
64 bytes from 192.168.0.10: icmp_seq=36 ttl=255 time=3.09 ms
64 bytes from 192.168.0.10: icmp_seq=37 ttl=255 time=3.12 ms
64 bytes from 192.168.0.10: icmp_seq=38 ttl=255 time=3.08 ms
64 bytes from 192.168.0.10: icmp_seq=39 ttl=255 time=2.65 ms

--- 192.168.0.10 ping statistics ---
39 packets transmitted, 39 received, 0% packet loss, time 38147ms
rtt min/avg/max/mdev = 2.608/3.104/8.904/0.964 ms
neil@Luna4:~$ 


I used the standard Epson 900 Color Stylus driver that was listed in the printer setup.  I've set this printer as Default -- it all appears to be working; but it doesn't print.

---

### Post by NeilBlanchard on 2007-03-02
Hello,

I got it working!  It was on "CUPS", but when I changed it to "HP DirectJet" and typed in the 192.168.010 address, it then printed out the Test Page!

:D 

Thank you.

Neil

---

### Post by courtier on 2007-07-18
I have three windows computers using a D-Link DP-301U network printer port to share a Samsung ML-1210 printer. To connect an ubuntu linux portable to use the same printer on the windows network I did the following using gnome, but only after considerable trial and error:

1) System-Administration-Printers-New Printer
2) Printer Type Radio button-network printer-Drop Down Box-TCP/Socket, HP Direct, Raw Connection
Forward
3) Host 192.168.0.7 (in my case more commonly 192.168.0.10, and I could not use the d-link port name) 
4) Port 2100 (entered for me but agrees with d-link web browser setup page)
Forward
5) Select manufacturer of printer from Drop Down Box
6) Select Model from list or use a disk
Forward
7) Choose name-description-location
Apply
Your printer will appear as ready in the Printers window

To alter these settings with immediate effect right click on your printer and use properties-connection

It took me a while to work this out but then I am a newbie

---

