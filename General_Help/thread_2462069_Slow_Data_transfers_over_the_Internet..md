---
title: "Slow Data transfers over the Internet."
date: 2021-05-12
forum: General Help
---

### Post by rsteinmetz70112 on 2021-05-12
I have been attempting to copy a lot data over the Internet 300-400GB 
I am having a lot of problems with speed. 

The sending machine hardware is Ubuntu 18.04 LTS (64 bit) with a 1 TB SATA RAID 1 array.
The Connection on that end is supposed to be Comcast 50MB/s down and 10 MB/s up. I gotten the full rated speed of upload to other sites.

The receiving end Hardware is a  computer running Ubuntu 18.04 (32bit) with a USB3 4TB External Drive
The Connection on that is is supposed to be ATT Fiber 100MB/s both directions.

Wired GB ethernet at both ends.

According to the receiving end I am only getting around 1.5 MiB/s throughput. 
That seems abysmally slow when neither computer seems to be particularly heavily loaded.

Any suggestions on locating the bottleneck?

---

### Post by TheFu on 2021-05-12
Use **rsync** and with --progress option.
Avoid using any GUI.

The sending machine has 10Mbps ... not MBps.  Network speeds are always Mbps (bits).  I typically see about 75% of whatever Comcast claims I should get on their optimized "speedtest" site.  Huge files being uploaded will probably be capped to 1Mbps to share the bandwidth.  If you use split and join on the files, you can send chunks of 10MB and "join" on the receiving side. This will mean that any disconnects or failures have minimal impact, especially if rsync is used.

For fun, I'm using speedtest-cli here:
```
$ speedtest-cli 
Retrieving speedtest.net configuration...
Testing from Comcast Business  (xx.xx.xx.xx)
Testing download speed................................................................................
Download: **29.60** Mbit/s
Testing upload speed................................................................................................
Upload: **6.06** Mbit/s
```

I pay for a 30/5 Mbps plan.  Let me check that on the last bill.  Ok, the bill doesn't actually say what speeds I'm supposed to get. There is a note about newer, faster, speeds being offered with a link.  I've never logged into this link.  It says:
```
INTERNET
25 Mbps / 5 Mbps
```
So today, I'm getting a faster connection than what I'm paying for. There is an "upgrade speed" link, which sadly is all marketing questions and the "submit" button is for someone to call and hassle me.  Nothing about their available plans. Had to click elsewhere for that.

Everything was pushing for personal contact - phone call/chat.
They do offer symetric ethernet service - 100/100 Mbps with 2 static IPs.  Hummmm. That is interesting to me, but nothing about pricing.  Last time I called was a few years ago and they wanted $450/month for 300 Mbps service with an $800 install fee.

If the connection is on Xfinity (residential service), then you get "best effort", no SLA.  I have an SLA, but it costs more.  When there is a problem, I get to a real person, in my country, fast.
This week, 
```
$ internet-up-summary.sh 
  Using /var/log/internet-up.log ... 
 Period 20210509-062611  - 20210512-171811
  Total Time: 4972 (min) 82.87 (hrs)
  Percent Up Time: 100.00 % 
  Percent Down Time: 0.00 % 
  Total Down Time: 0 min or 0.00 hrs
 Currently: UP
```

Last week, the connection was down 14 minutes - well, the connection monitoring was down 14 minutes OR the connection was down.  I did some router firmware upgrades which needed a few reboots last week - easily 14 minutes of downtime and probably my fault.

---

