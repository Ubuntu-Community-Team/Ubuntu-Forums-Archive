---
title: "How to check broadband speed"
date: 2018-12-24
forum: General Help
---

### Post by satimis on 2018-12-24
Hi all,

Desktop PC Spec
AMD 8-core CPU
RAM 32G
HD  2TB SSD
Network Card  1G

FTTH Broadband - Symmetrical Connection
500M up/down

OS
&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial

```

Recently I found the speed of my FTTH Broadband is slow on browsing Internet.  I don't know whether it is the speed problem of my FTTH Broadband or the problem of the websites being browsed.

Please advise which will be the reliable way checking broadband speed.

Thanks in advance.

Regards
satimis

---

### Post by ajgreeny on 2018-12-24
You can try these two websites which will show you ping times, download and upload speeds very clearly.
[http://www.speedtest.net/](http://www.speedtest.net/)
[http://www.broadbandspeedchecker.co.uk/](http://www.broadbandspeedchecker.co.uk/)

You can also do it in command line but at the moment I can not find the command to use, and the one I used in the past ```
wget -O - https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py | python

``` no longer works.

EDIT:
I have found the command to use which does work ```
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
```

Since 16.04 **speedtest-cli** is in Ubuntu repositories now. For Ubuntu 16.04 (Xenial) and later use:

```
sudo apt install speedtest-cli
speedtest-cl
```

---

### Post by satimis on 2018-12-24
> **ajgreeny said:**
> You can try these two websites which will show you ping times, download and upload speeds very clearly.
[http://www.speedtest.net/](http://www.speedtest.net/)
[http://www.broadbandspeedchecker.co.uk/](http://www.broadbandspeedchecker.co.uk/)

You can also do it in command line but at the moment I can not find the command to use, and the one I used in the past ```
wget -O - https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py | python

``` no longer works.

EDIT:
I have found the command to use which does work ```
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
```

Since 16.04 **speedtest-cli** is in Ubuntu repositories now. For Ubuntu 16.04 (Xenial) and later use:

```
sudo apt install speedtest-cli
speedtest-cl
```

Hi,

Thanks for your advice.  Performed following tests;


1)
[http://www.speedtest.net/](http://www.speedtest.net/)

1st Test
======
Ping ms	2
Download Mbps	474.79
Upload Mbps	483.57 

NETVIGATOR (service provider)
Star shown (on the left)
- very unhappy

2nd Test
=======
Ping ms	3
Download Mbps	461.61
Upload Mbps	485.24 


2)
[https://www.broadbandspeedchecker.co.uk/](https://www.broadbandspeedchecker.co.uk/)

1st Test
======
Ping	    Download	 Upload
9 ms    243.20 Mb/s	 214.65 Mb/s

Netvigator (service provider)


2nd Test
========
Ping	       Download	        Upload
13 ms      313.87 Mb/s      221.39 Mb/s


There are big difference in the test results


3)
1st Test
======
&#10219; curl -s [https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py](https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py) | python -
Retrieving speedtest.net configuration...```

Testing from Netvigator .......
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by STC (Hong Kong) [4.08 km]: 4.449 ms
Testing download speed................................................................................
Download: 0.43 Mbit/s
Testing upload speed................................................................................................
Upload: 0.24 Mbit/s

```


2nd Test
======
- Shut down the desktop PC
- Turned the ONT (Optical Network Terminal) off and then on again
- Turned the router off and then on again
- Boot up the desktop PC

&#10219; curl -s [https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py](https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py) | python -```

Retrieving speedtest.net configuration...
Testing from Netvigator ........
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by STC (Hong Kong) [4.08 km]: 4.637 ms
Testing download speed................................................................................
Download: 0.36 Mbit/s
Testing upload speed................................................................................................
Upload: 0.50 Mbit/s

```


[https://www.broadbandspeedchecker.co.uk/](https://www.broadbandspeedchecker.co.uk/)
Ping	      Download       Upload
186 ms   186.70 Mb/s   21.69 Mb/s


[http://www.speedtest.net/](http://www.speedtest.net/)
Ping ms	254
Download Mbps	249.17
Upload Mbps	58.52 


Install speedtest-cli
&#10219; speedtest-cli```

Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Netvigator .......
Selecting best server based on latency...
Hosted by STC (Hong Kong) [4.08 km]: 3.955 ms
Testing download speed........................................
Download: 1.62 Mbit/s
Testing upload speed..................................................
Upload: 2.28 Mbit/s

```

My paid broadband speed   500 Mb/s

Shall I contact the service provider informing them the checking results ?  Thanks

Regards
satimis

---

