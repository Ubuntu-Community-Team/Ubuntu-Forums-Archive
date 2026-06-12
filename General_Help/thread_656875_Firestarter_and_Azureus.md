---
title: "Firestarter and Azureus"
date: 2008-01-03
forum: General Help
---

### Post by MeanStreak on 2008-01-03
Hi,

I foolishly, or not, installed Azureus and configured Firestarter's policy to accept an incoming port for PnP sharing, etc. I've now removed Azureus from my machine, but I'm seeing a lot of blocked connections (mostly UDP)  banking up in the Events tab of Firestarter. What's happened? In configuring Azureus have I broadcast my box to every hacker in the known universe?

Here's a copy of the log:

> Time:Jan  3 17:30:30 Direction: Unknown In:eth0 Out: Port:47853 Source:207.191.211.30 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:31 Direction: Unknown In:eth0 Out: Port:47853 Source:70.55.126.80 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:33 Direction: Unknown In:eth0 Out: Port:47853 Source:70.65.7.14 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:35 Direction: Unknown In:eth0 Out: Port:47853 Source:85.146.0.194 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:35 Direction: Unknown In:eth0 Out: Port:47853 Source:68.119.110.10 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:35 Direction: Unknown In:eth0 Out: Port:47853 Source:24.27.182.16 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:36 Direction: Unknown In:eth0 Out: Port:47853 Source:83.11.231.46 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:37 Direction: Unknown In:eth0 Out: Port:47853 Source:87.187.90.19 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:39 Direction: Unknown In:eth0 Out: Port:47853 Source:206.248.228.10 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:40 Direction: Unknown In:eth0 Out: Port:47853 Source:74.78.32.223 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:40 Direction: Unknown In:eth0 Out: Port:47853 Source:68.222.204.37 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:40 Direction: Unknown In:eth0 Out: Port:47853 Source:86.136.253.147 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:40 Direction: Unknown In:eth0 Out: Port:47853 Source:67.149.130.199 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:42 Direction: Unknown In:eth0 Out: Port:47853 Source:85.31.186.193 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:44 Direction: Unknown In:eth0 Out: Port:47853 Source:83.19.173.42 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:44 Direction: Unknown In:eth0 Out: Port:47853 Source:87.123.94.160 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:45 Direction: Unknown In:eth0 Out: Port:47853 Source:74.78.32.223 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:45 Direction: Unknown In:eth0 Out: Port:47853 Source:68.35.151.180 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:45 Direction: Unknown In:eth0 Out: Port:47853 Source:195.218.13.62 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:46 Direction: Unknown In:eth0 Out: Port:47853 Source:77.161.183.80 Destination:10.0.0.1 Length:86 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:46 Direction: Unknown In:eth0 Out: Port:47853 Source:81.62.11.115 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:47 Direction: Unknown In:eth0 Out: Port:47853 Source:86.220.111.150 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:47 Direction: Unknown In:eth0 Out: Port:47853 Source:83.101.1.160 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:48 Direction: Unknown In:eth0 Out: Port:47853 Source:99.246.165.253 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:49 Direction: Unknown In:eth0 Out: Port:47853 Source:68.194.129.176 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:51 Direction: Unknown In:eth0 Out: Port:47853 Source:69.221.235.148 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:53 Direction: Unknown In:eth0 Out: Port:47853 Source:196.212.85.146 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:55 Direction: Unknown In:eth0 Out: Port:47853 Source:87.180.46.48 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:56 Direction: Unknown In:eth0 Out: Port:47853 Source:83.45.136.109 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:58 Direction: Unknown In:eth0 Out: Port:47853 Source:82.247.50.66 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:58 Direction: Unknown In:eth0 Out: Port:47853 Source:88.117.76.16 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:59 Direction: Unknown In:eth0 Out: Port:47853 Source:220.236.156.156 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:30:59 Direction: Unknown In:eth0 Out: Port:47853 Source:96.2.191.97 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:02 Direction: Unknown In:eth0 Out: Port:47853 Source:83.19.173.42 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:02 Direction: Unknown In:eth0 Out: Port:47853 Source:88.66.93.98 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:03 Direction: Unknown In:eth0 Out: Port:47853 Source:85.225.210.23 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:05 Direction: Unknown In:eth0 Out: Port:47853 Source:24.158.125.225 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:07 Direction: Unknown In:eth0 Out: Port:47853 Source:84.115.65.126 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:07 Direction: Unknown In:eth0 Out: Port:47853 Source:89.53.202.201 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:08 Direction: Unknown In:eth0 Out: Port:47853 Source:84.182.233.65 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:10 Direction: Unknown In:eth0 Out: Port:47853 Source:86.220.111.150 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:12 Direction: Unknown In:eth0 Out: Port:47853 Source:85.168.151.7 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:17 Direction: Unknown In:eth0 Out: Port:47853 Source:70.109.218.167 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:19 Direction: Unknown In:eth0 Out: Port:47853 Source:84.61.207.117 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:19 Direction: Unknown In:eth0 Out: Port:47853 Source:85.146.0.194 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:20 Direction: Unknown In:eth0 Out: Port:47853 Source:99.224.150.47 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:20 Direction: Unknown In:eth0 Out: Port:47853 Source:85.146.0.194 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:21 Direction: Unknown In:eth0 Out: Port:47853 Source:89.10.30.160 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:23 Direction: Unknown In:eth0 Out: Port:47853 Source:75.62.5.79 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:27 Direction: Unknown In:eth0 Out: Port:47853 Source:85.146.0.194 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:28 Direction: Unknown In:eth0 Out: Port:47853 Source:78.96.95.43 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:29 Direction: Unknown In:eth0 Out: Port:47853 Source:85.75.83.99 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:31 Direction: Unknown In:eth0 Out: Port:47853 Source:68.39.73.159 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:32 Direction: Unknown In:eth0 Out: Port:47853 Source:86.33.161.65 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:32 Direction: Unknown In:eth0 Out: Port:47853 Source:92.249.136.236 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:34 Direction: Unknown In:eth0 Out: Port:47853 Source:209.91.206.177 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:35 Direction: Unknown In:eth0 Out: Port:47853 Source:83.81.32.244 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:37 Direction: Unknown In:eth0 Out: Port:47853 Source:86.220.111.150 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:38 Direction: Unknown In:eth0 Out: Port:47853 Source:211.128.85.129 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:38 Direction: Unknown In:eth0 Out: Port:47853 Source:24.10.175.208 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:40 Direction: Unknown In:eth0 Out: Port:47853 Source:86.220.111.150 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:43 Direction: Unknown In:eth0 Out: Port:47853 Source:85.146.0.194 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:45 Direction: Unknown In:eth0 Out: Port:47853 Source:87.20.184.213 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:45 Direction: Unknown In:eth0 Out: Port:47853 Source:89.10.30.160 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:45 Direction: Unknown In:eth0 Out: Port:47853 Source:90.196.173.26 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:46 Direction: Unknown In:eth0 Out: Port:47853 Source:82.83.141.173 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:47 Direction: Unknown In:eth0 Out: Port:47853 Source:79.213.221.156 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:48 Direction: Unknown In:eth0 Out: Port:47853 Source:68.102.78.168 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:49 Direction: Unknown In:eth0 Out: Port:47853 Source:81.152.152.67 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:50 Direction: Unknown In:eth0 Out: Port:47853 Source:70.55.102.251 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:50 Direction: Unknown In:eth0 Out: Port:47853 Source:76.104.225.52 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:50 Direction: Unknown In:eth0 Out: Port:47853 Source:195.38.100.188 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:51 Direction: Unknown In:eth0 Out: Port:47853 Source:76.104.225.52 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:51 Direction: Unknown In:eth0 Out: Port:47853 Source:207.161.187.3 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:51 Direction: Unknown In:eth0 Out: Port:47853 Source:83.81.73.31 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:52 Direction: Unknown In:eth0 Out: Port:47853 Source:41.221.19.137 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:52 Direction: Unknown In:eth0 Out: Port:47853 Source:81.102.130.177 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:53 Direction: Unknown In:eth0 Out: Port:47853 Source:79.138.172.92 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:54 Direction: Unknown In:eth0 Out: Port:47853 Source:88.12.218.77 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:54 Direction: Unknown In:eth0 Out: Port:47853 Source:151.197.178.238 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:31:55 Direction: Unknown In:eth0 Out: Port:47853 Source:80.102.129.44 Destination:10.0.0.1 Length:85 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:00 Direction: Unknown In:eth0 Out: Port:47853 Source:89.181.106.9 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:01 Direction: Unknown In:eth0 Out: Port:47853 Source:207.81.51.121 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:01 Direction: Unknown In:eth0 Out: Port:47853 Source:89.245.76.140 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:01 Direction: Unknown In:eth0 Out: Port:47853 Source:213.136.116.17 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:01 Direction: Unknown In:eth0 Out: Port:47853 Source:89.79.173.152 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:02 Direction: Unknown In:eth0 Out: Port:47853 Source:196.212.85.146 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:02 Direction: Unknown In:eth0 Out: Port:47853 Source:90.227.153.248 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:03 Direction: Unknown In:eth0 Out: Port:47853 Source:220.142.0.157 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:04 Direction: Unknown In:eth0 Out: Port:47853 Source:67.182.255.92 Destination:10.0.0.1 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:05 Direction: Unknown In:eth0 Out: Port:47853 Source:60.242.246.249 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:05 Direction: Unknown In:eth0 Out: Port:47853 Source:189.54.2.47 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:06 Direction: Unknown In:eth0 Out: Port:47853 Source:86.220.111.150 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:06 Direction: Unknown In:eth0 Out: Port:47853 Source:66.38.55.242 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:07 Direction: Unknown In:eth0 Out: Port:47853 Source:24.235.229.113 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:07 Direction: Unknown In:eth0 Out: Port:47853 Source:212.40.87.117 Destination:10.0.0.1 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan  3 17:32:07 Direction: Unknown In:eth0 Out: Port:47853 Source:75.53.115.221 Destination:10.0.0.1 Length:70 TOS:0x00 Protocol:UDP Service:Unknown

---

### Post by heimo on 2008-01-03
> **MeanStreak said:**
> In configuring Azureus have I broadcast my box to every hacker in the known universe?

Your address is now probably in a cache / memory of other p2p clients, which will try to connect to your box until some expiration time has passed. Shouldn't harm you (much). :-)

---

### Post by MeanStreak on 2008-01-03
Thanks for that - just the kind of answer I was after. I can now rest assured (somewhat). :)

---

