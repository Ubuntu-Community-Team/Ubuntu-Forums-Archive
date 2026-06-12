---
title: "command line SpeedTest Client Not working due to an SSL certificate error"
date: 2024-08-08
forum: General Help
---

### Post by crpz41 on 2024-08-08
I run ubuntu server 22.04 and my platform is armhf. I run the speedtest  client version 1.0.0.2-1.5ae238b 
speedtest is the ookla program to run internt speedtests. it's not the 3rd party speedtest-cli.

 I get the following certificate  error after launching the program: 

speedtest 
[2024-08-09 00:47:25.496] [error] Configuration - SSL peer certificate  or SSH remote key was not OK (UnknownException) 
[2024-08-09 00:47:25.496] [error] Configuration - Cannot retrieve  configuration document (0) 
[2024-08-09 00:47:25.497] [error] ConfigurationError - Could not  retrieve or read configuration (Configuration) 
[2024-08-09 00:47:25.497] [error] ConfigurationError - Could not  retrieve or read configuration (Configuration) 
[error] Configuration - Could not retrieve or read configuration  (ConfigurationError) 


I haven't changed anything in the system lately, the program stopped  working suddenly during the night (its execution is automated). I tried  multiple potential fixes including updating ca-certificates and installing libssl1.1_1.1.1w-0+deb11u1, looking for updates. 

I ran out of ideas. no  other program on the system has SSL certificate errors, I know speedtest user curl to connect so this issue is somewhat related to curl not liking certificates.

let me know how can this be fixed

---

### Post by TheFu on 2024-08-08
Wait a day and try again.
Repeat.

---

### Post by currentshaft on 2024-08-09
25

---

### Post by crpz41 on 2024-08-09
this is the official speedtest command line app from ookla. now I updated to the latest version

available here:

[https://www.speedtest.net/apps/cli](https://www.speedtest.net/apps/cli)

---

### Post by currentshaft on 2024-08-09
g

---

### Post by crpz41 on 2024-08-09
speedtest-cli returns lower results for some reason (less than 300 mbps), maybe it's not very much optimized for my slow arm processor in the raspberry. if I can't test the potential full gigabit of the connection, keeping logs stop make sense. I need to recover the use of the old one.

I noticed, if you restart the network service the speedtest works for a few minutes. would be cool to know why. other network related services work just fine.

---

### Post by him610 on 2024-08-09
```

$ apt show speedtest-cli
Package: speedtest-cli
Version: 2.1.3-2
Priority: optional
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Jonathan Carter <jcc@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 106 kB
Depends: python3:any, python3-pkg-resources, ca-certificates
Homepage: https://github.com/sivel/speedtest-cli/
Download-Size: 24.1 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
Description: Command line interface for testing internet bandwidth using speedtest.net
 Speedtest.net is a webservice that allows you to test your broadband
 connection by downloading a file from one of many Speedtest.net
 servers from around the world.
 .
 This utility allows you to use the Speedtest.net service from the
 command line.
 .
 Note: This tool accesses speedtest.net over http, while the web-based client
 uses websockets. This tool has shown to become increasingly inacurate with
 high-speed connections. For more information, see the readme on:
 https://github.com/sivel/speedtest-cli

```

---

### Post by him610 on 2024-08-09
```
$ speedtest-cli &
[1] 156644
....:~$ Retrieving speedtest.net configuration...
Testing from Comcast Cable (xxx.xx.xxx.x)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Shentel (Ashburn, VA) [93.31 km]: 68.035 ms
Testing download speed................................................................................
Download: 79.57 Mbit/s
Testing upload speed......................................................................................................
Upload: 22.57 Mbit/s

[1]+  Done                    speedtest-cli
 
```

---

### Post by TheFu on 2024-08-09
Different models of Raspberry Pi hardware have different limitations on bandwidth, regardless of what the spec sheet says.  Some with "GigE" ports can only get at most 250Mbps because that GigE port is internally connected to a USB2 bus.

So, what exact version of Rapberry Pi and which exact version of an OS is being used?  Those are the first two questions to be answered.  I see 22.04 but is that desktop Ubuntu or Server or Core?

---

### Post by crpz41 on 2024-08-10
notes on the system:
I have ubuntu 22.04 server, there is no GUI.
the raspberry is the Pi4 4GB RAM. for the task I do, it's overkill.
I use max 512MB of RAM and I hit 100% cpu usage only during security  updates. the other network services use very low bandwidth and cpu.
it's basically a network QoS monitoring device with few services available for local users (for example Pihole)

back to the speedtest problem:

with the regular speedtest program I can hit 940 mbps download, the cpu usage goes mainly on 1-2 cores, it's not heavy at all. I don't know why the cli version cannot perform the same, we are here to find why the regular app see network problems.
the problem isn't the app, it's something in the system of course related to certificates and access to the network. we shouldn't focus on the speedtest program itself.

---

### Post by TheFu on 2024-08-10
I have a pi4 (and 3, 2, zero ... and some other SBCs for specialized uses).  

My pi4 has a wired ethernet and runs Debian 11.
Between a Ryzen desktop going through 2 GigE switches, I'm seeing:
```
$ iperf3 -c pi4
Connecting to host pi4, port 5201
[  5] local 172.22.22.6 port 42878 connected to 172.22.22.17 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   957 Mbits/sec    0    389 KBytes       
[  5]   1.00-2.00   sec   112 MBytes   942 Mbits/sec    0    389 KBytes       
[  5]   2.00-3.00   sec   112 MBytes   942 Mbits/sec    0    389 KBytes       
[  5]   3.00-4.00   sec   112 MBytes   943 Mbits/sec    0    410 KBytes       
[  5]   4.00-5.00   sec   112 MBytes   939 Mbits/sec    0    431 KBytes       
[  5]   5.00-6.00   sec   113 MBytes   947 Mbits/sec    0    498 KBytes       
[  5]   6.00-7.00   sec   112 MBytes   941 Mbits/sec    0    522 KBytes       
[  5]   7.00-8.00   sec   112 MBytes   944 Mbits/sec    0    604 KBytes       
[  5]   8.00-9.00   sec   112 MBytes   944 Mbits/sec    0    632 KBytes       
[  5]   9.00-10.00  sec   112 MBytes   940 Mbits/sec    0    663 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.10 GBytes   944 Mbits/sec    0             sender
[  5]   0.00-10.04  sec  1.10 GBytes   938 Mbits/sec                  receiver

iperf Done.
```
That's quite respectable network transfers.  No storage is involved.  My pi4 doesn't have any storage except a microSD with the OS. All data it uses is either streamed or via NFS mounts.

I installed the debian speedtest-cli to run this test:
```
$ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Comcast Business (50.xxx.xxx.xxx)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by GSL Networks (Atlanta, GA) [28.43 km]: 23.184 ms
Testing download speed................................................................................
Download: 28.89 Mbit/s
Testing upload speed......................................................................................................
Upload: 6.00 Mbit/s
```
That's what I'd expect for my connection.  I should have 30/6 Mbps.
My WAN router won't go faster than about 650 Mbps based on testing I did before putting it into production in 2015-ish.  It is an APU2 SBC, purpose built as a router with a low-power AMD 64-bit CPU and 4 Intel i210 NICs.  On BSD, the Intel NIC drivers don't automatically go multithreaded.  If I have 4 different network transfers going, then I can get to 1Gbps total, but not for a single stream.

Anyway, my initial suggestion was to wait a day and test again. Did that solve it?  These speedtest servers are often down/misconfigured, so unless you specify a specific one to use, it is luck of the draw.

---

### Post by currentshaft on 2024-08-10
.

---

### Post by crpz41 on 2024-08-10
so you thought it was a speedtest server related issue, of course not otherwise we would not talk right now. 
there is some network bug of some sort in my OS that prevents the app from connecting to the internet.
among all possible software we didn't mention, a firewall would be a good question, but it's not enabled.

the most useful information we have at the moment is one sentence I said yesterday, if you restart the network the speedtest starts without problem (**sudo systemctl restart NetworkManager.service**)

then after 1 min I get the certificate error again.
this tells us clearly there is something wrong with the OS networking yet I don't know what it is.

---

### Post by crpz41 on 2024-08-10
if you check the first post I made you see the output. I re post it here

speedtest 
[2024-08-09 00:47:25.496] [error] Configuration - SSL peer certificate  or SSH remote key was not OK (UnknownException) 
[2024-08-09 00:47:25.496] [error] Configuration - Cannot retrieve  configuration document (0) 
[2024-08-09 00:47:25.497] [error] ConfigurationError - Could not  retrieve or read configuration (Configuration) 
[2024-08-09 00:47:25.497] [error] ConfigurationError - Could not  retrieve or read configuration (Configuration) 
[error] Configuration - Could not retrieve or read configuration  (ConfigurationError)


your question made me retry a test and I am getting a different error right now:

speedtest 
[2024-08-10 22:05:09.557] [error] Configuration - Couldn't connect to server (Network is unreachable)
[2024-08-10 22:05:09.558] [error] Configuration - Cannot retrieve configuration document (0)
[2024-08-10 22:05:09.558] [error] ConfigurationError - Could not retrieve or read configuration (Configuration)
[2024-08-10 22:05:09.558] [error] ConfigurationError - Could not retrieve or read configuration (Configuration)
[error] Configuration - Could not retrieve or read configuration (ConfigurationError)

please remember the program works fine, for the reason I explain to theFu. this new error gives new insights

---

### Post by TheFu on 2024-08-10
> **crpz41 said:**
>  
this tells us clearly there is something wrong with the OS networking yet I don't know what it is.

Actually, that error doesn't tell me what you seem to think it says.  But you seem to know the problem, so I'll stop guessing.

---

### Post by currentshaft on 2024-08-10
.

---

### Post by crpz41 on 2024-08-11
the program used to work and now it doesn't work, no system changes have been made.

reproducing the issue with cli doesn't make any sense because they are different programs, cli works and since it performs worse on my system so I can't use it. sorry for that.

I am not investigating the program itself rather the system conditions that doesn't make it functional. I am not concerned that ookla one is a closed source, I just want something that works as it used to work for years. I really hope that someone here is able to help people for this issue.

---

### Post by currentshaft on 2024-08-11
.

---

### Post by crpz41 on 2024-08-11
I had these updates available for the system, afterwards the program works again.

Preparing to unpack .../python3-problem-report_2.20.11-0ubuntu82.6_all.deb ...
Unpacking python3-problem-report (2.20.11-0ubuntu82.6) over (2.20.11-0ubuntu82.5) ...
Preparing to unpack .../python3-apport_2.20.11-0ubuntu82.6_all.deb ...
Unpacking python3-apport (2.20.11-0ubuntu82.6) over (2.20.11-0ubuntu82.5) ...
Preparing to unpack .../apport_2.20.11-0ubuntu82.6_all.deb ...
Unpacking apport (2.20.11-0ubuntu82.6) over (2.20.11-0ubuntu82.5) ...
Setting up python3-problem-report (2.20.11-0ubuntu82.6) ...
Setting up python3-apport (2.20.11-0ubuntu82.6) ...
Setting up apport (2.20.11-0ubuntu82.6) ...

---

