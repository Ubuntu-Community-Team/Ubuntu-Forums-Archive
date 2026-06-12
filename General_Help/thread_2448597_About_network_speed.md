---
title: "About network speed"
date: 2020-08-10
forum: General Help
---

### Post by satimis on 2020-08-10
Hi all

Ubuntu 18.04

My home network is connected to FTTH symmetric network with 500M UP/DOWN speed.

On Terminal running speed test
$ speedtest-cli --simple```

Ping: 2.13 ms
Download: 437.53 Mbit/s
Upload: 4.15 Mbit/s

```
It shows the upload speed being only 4.15 Mbit/s

I can't resolved it is only about 1/10 of the guaranteed speed?  Please advise whether I need uploading files to test?

Regards

---

### Post by ActionParsnip on 2020-08-10
What is your contention ration and did you run the test at peak time?

---

### Post by satimis on 2020-08-10
> **ActionParsnip said:**
> What is your contention ration and did you run the test at peak time?
Hi,

I was the only user using the broadband

I did the test at about 11 pm, almost mid-night NOT peak time here.

I did the test again now;
$ speedtest-cli --simple```

Ping: 3.851 ms
Download: 451.72 Mbit/s
Upload: 4.15 Mbit/s

```

It is 04:24 hrs before morning here.  Also I'm the only user.

Remark:
Only one PC is connected to the network via wired router

Regards

---

### Post by TheFu on 2020-08-10
Most broadband upload issues are for an entire neighborhood, not just a single house/apartment.  Because most people download stuff 1000x more than they upload, the networks are tuned for that workload. If you want symmetric bandwidth, some ISPs provide that, for a price.  Most of us are happy with asymmetric bandwidth for the significant cost savings.

On the bill, it should clearly say what "offer" the connection is under.  I'm staring at my bill now. It says "Starter" and "business internet" and "Static, IP - 5".  So if I visit the ISP's pages and look for "Starter" in the business area, it shows ... 
"Speeds up to 35/5 Mbps Internet"

speedtest-cli returns:
> Download: 26.99 Mbit/s
Upload: 5.88 Mbit/s

Watching some streaming video at the same time.  I've seen the download over 32Mbps previously.

---

### Post by satimis on 2020-08-11
> **TheFu said:**
> Most broadband upload issues are for an entire neighborhood, not just a single house/apartment.  Because most people download stuff 1000x more than they upload, the networks are tuned for that workload. If you want symmetric bandwidth, some ISPs provide that, for a price.  Most of us are happy with asymmetric bandwidth for the significant cost savings.

On the bill, it should clearly say what "offer" the connection is under.  I'm staring at my bill now. It says "Starter" and "business internet" and "Static, IP - 5".  So if I visit the ISP's pages and look for "Starter" in the business area, it shows ... 
"Speeds up to 35/5 Mbps Internet"

speedtest-cli returns:

Watching some streaming video at the same time.  I've seen the download over 32Mbps previously.
Hi,

Thanks for your advice.

The current (30 months) contract of subscription shall be expired at end of coming Sept (next month).  

The monthly bill is very simple```

BILL DETAILS
Service Charges
Period/Date 	22/05 - 21/06
Description	Broadband &/or Now TV Bundle Service Fee
......

```

I just rechecked the service contract.  I have captured the part in re bandwidth and attached the photo here.

At time of negotiation the Sales confirmed that it was a symmetrical FTTH of 500M speed.  It was my mistake not reading the contract carefully.  Now I have learned a lesson.  I'll pay more attention on the terms of the contract rather than trusting the Sales.

I may change ISP.

Regards

---

