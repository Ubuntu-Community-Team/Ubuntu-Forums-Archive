---
title: "lm-sensors working, sensord not."
date: 2007-08-18
forum: General Help
---

### Post by DaveFP on 2007-08-18
I'm going to be performing some stress tests on my system in the near future so I wanted to install a means of reading/logging the system temperatures. I successfully installed lm-sensors via apt-get and then ran the 'detect-sensors' script. After this, invoking 'sensors' displays (I assume) correct temperatures and fan speeds for everything.

I then installed 'sensord', also using apt-get. However, upon starting the sensord daemon and then checking the log file that I'm redirecting output to (from instructions on the lm-sensors wiki) I get the following error:

```

Aug 18 00:53:22 Atlantis sensord: sensord started
Aug 18 00:53:22 Atlantis sensord: Chip: k8temp-pci-00c3
Aug 18 00:53:22 Atlantis sensord: Adapter: PCI adapter
Aug 18 00:53:22 Atlantis sensord:   Core0 Temp: 29.00
Aug 18 00:53:22 Atlantis sensord: Error getting sensor data: k8temp/temp2: Can'$
Aug 18 00:53:22 Atlantis sensord: sensord failed

```

Far from ideal. Has anyone else had a similar problem or managed to get a log working properly? If it comes to it I guess I could always write a script to repeatedly call 'sensors' and just capture the results but I would much rather use the built in logging if at all possible. Thanks!

System is an Athlon 64 3800+ on an ASUS A8N-VM mobo. I'm running 64bit 7.06 server with 32bit compatibility libraries.

---

