---
title: "Can't Ping, load or access Google.com and other Google Domains"
date: 2008-05-10
forum: General Help
---

### Post by jeffimperial on 2008-05-10
This is pretty weird. I have been submerged all night in #ubuntu and no one's been able to help me.

Problem:
I cannot, repeat cannot, load Google.com or any of its other domains (including analytics, gmail, calendar and everything else). All other sites that I frequent seem to work fine. Pinging it simply returns a Request Timed Out error. I find it quite hard to believe that Google's servers are too busy to not be able to return my calls.

**TEST REULTS. Host, TraceRoute Google**

```
jeff@jeff-linux:~$ host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 64.233.189.104
www.l.google.com has address 64.233.189.99
www.l.google.com has address 64.233.189.147
jeff@jeff-linux:~$ traceroute 64.233.189.104
traceroute to 64.233.189.104 (64.233.189.104), 30 hops max, 40 byte packets
1  202.78.96.212 (202.78.96.212)  17.714 ms  19.599 ms  19.572 ms
2  202.78.96.210 (202.78.96.210)  31.563 ms  31.541 ms  31.501 ms
3  202.78.96.210 (202.78.96.210)  33.395 ms  33.372 ms  33.338 ms
4  202.78.96.94 (202.78.96.94)  37.293 ms  41.263 ms  41.244 ms
5  202.78.96.94 (202.78.96.94)  41.213 ms  41.182 ms  45.103 ms
6  202.78.101.250 (202.78.101.250)  45.077 ms  20.867 ms  24.310 ms
7  203.177.48.153 (203.177.48.153)  24.221 ms  32.175 ms  50.205 ms
8  203.177.31.37 (203.177.31.37)  52.124 ms  52.100 ms  52.068 ms
9  203.177.26.237 (203.177.26.237)  94.017 ms  95.932 ms  95.906 ms
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```


**TracePath Google**

```
jeff@jeff-linux:~$ tracepath 64.233.189.104
1:  121.96.213.56.bti.net.ph (121.96.213.56)               0.296ms pmtu 1492
1:  202.78.96.212 (202.78.96.212)                         37.849ms 
1:  202.78.96.212 (202.78.96.212)                         39.150ms 
2:  202.78.96.210 (202.78.96.210)                         40.076ms asymm  6 
3:  202.78.96.210 (202.78.96.210)                         46.192ms asymm  6 
4:  202.78.96.94 (202.78.96.94)                           40.194ms asymm  2 
5:  202.78.96.94 (202.78.96.94)                           40.549ms asymm  2 
6:  202.78.101.250 (202.78.101.250)                       41.966ms asymm  3 
7:  203.177.48.153 (203.177.48.153)                       41.832ms asymm  4 
8:  203.177.31.37 (203.177.31.37)                         43.498ms asymm  5 
9:  203.177.26.237 (203.177.26.237)                      104.053ms asymm  6 
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1492
     Resume: pmtu 1492 
```


**OTHER DETAILS that might help shed some light to anyone who has an idea:**
[LIST=1]
[*]I am not using OpenDNS as far as I know
[*]I am not behind a firewall, personally set up or institutional (like in schools and businesses)
[*]Last things I did before this started happening were: Add an ntpdate file to correct my system clock (which did not work out), add my Google Calendar to Evolution Mail (which I have removed, no change), and installed LAMP.
[*]This problem persists even in Opera, and I also cannot get to Google in my Dual-boot Windows installation. But please note that this started happening ONLY after I started using Ubuntu, after I upgraded to Hardy. I'm not putting blame on Ubuntu or Hardy. I just wanna figure out what's going on.
[*]I am not behind a router. I connect via PPPoE and a Huawei SmartAX MT880 modem.
[/LIST]


My ISP is not claiming responsibility. Any kind of help will be much appreciated.

---

### Post by jeffimperial on 2008-05-10
ok.. I just found a solution to my misery and I hope this helps. I have been told that "google's dns seems to resolve differently on different nameservers.  My current DNS servers may be the problem"

here's what I did:
[LIST=1]
[*]Took note of the two ISP-provided DNS addresses.
[*]Deleted those two ISP-provided DNS addresses.
[*]Added OpenDNS addresses: **208.67.222.222** and **208.67.220.220**
[*]Added back the ones I deleted (this was because I was advised to have OpenDNS addresses at higher list priority)
[/LIST]

So now, everything back to normal. I hope this status-quo does not change any time soon. And I hope this helps other guys out there!

---

